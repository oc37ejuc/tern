# Copyright (c) 2019 VMware, Inc. All Rights Reserved.
# SPDX-License-Identifier: BSD-2-Clause

FROM photon:3.0

# install system dependencies
# photon:3.0 comes with toybox which conflicts with some dependencies needed for tern to work, so uninstalling
# toybox first
RUN tdnf remove -y toybox && tdnf install -y tar findutils attr util-linux python3 python3-pip python3-setuptools git

# install pip
RUN pip3 install --upgrade pip

# install tern with latest changes
COPY dist/tern-*.tar.gz .
RUN pip install tern-*.tar.gz

# make a mounting directory
RUN mkdir hostmount

ENTRYPOINT ["tern", "-b", "/hostmount"]
CMD ["-h"]
