# Sometimes it's a README fix, or something like that - which isn't relevant for
# including in a project's CHANGELOG for example
has_source_changes = !modified_files.grep(/Classes/).empty?

# Make a note about contributors not in the organization
octo_client = env.request_source.client
unless octo_client.organization_member?('bitstadium', pr_author)
end

declared_trivial = pr_labels.include?("#trivial") || !has_source_changes
if !modified_files.include?("CHANGELOG.md") && !declared_trivial
  fail "Please include a CHANGELOG entry. \nYou can find it at [CHANGELOG.md](https://github.com/bitstadium/HockeySDK-iOS/blob/develop/CHANGELOG.md)."
end

# Make it more obvious that a PR is a work in progress and shouldn't be merged yet
warn "PR is classed as Work in Progress" if pr_title.include? "[WIP]"

# Warn when there is a big PR
warn "Big PR" if lines_of_code > 250

if pr_body.length < 5
  fail "Please provide a summary in the Pull Request description"
end
