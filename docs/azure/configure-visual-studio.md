---
title: .NET ile Azure geliştirme için Visual Studio 'Yu yapılandırma
description: Bu makalede, Visual Studio 'nun yüklü olduğu ve Azure hesabınıza bağlanması dahil olmak üzere Azure için Visual Studio geliştirme 'yi yapılandırmanıza yardımcı olur
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 986469bd07657d968045465803047dc21d76dd62
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701223"
---
# <a name="configure-visual-studio-for-azure-development-with-net"></a>.NET ile Azure geliştirme için Visual Studio 'Yu yapılandırma

Visual Studio, Azure 'da uygulamaların geliştirilmesine ve dağıtımına yardımcı olan araçları içerir.  Bu kılavuz, Azure geliştirmesi için Visual Studio 'Yu doğru şekilde yapılandırdığınızdan emin olmanıza yardımcı olur.

### <a name="download-visual-studio-2019"></a>Visual Studio 2019’u İndirin

Visual Studio 2019 zaten yüklüyse, bu adımı atlayabilirsiniz.

> [!div class="nextstepaction"]
> [Visual Studio 2019’u İndirin](https://www.visualstudio.com/downloads/)

### <a name="install-azure-workloads"></a>Azure iş yüklerini yükler

**Visual Studio yükleyicisi** başlatın ve **Azure geliştirme** ve **ASP.net ve Web geliştirme** iş yüklerinin yüklü olduğunu doğrulayın.  Bu iş yüklerinden herhangi biri yüklü değilse, yüklemek için bu iş yüklerini seçin.

![Azure geliştirme ve ASP.NET ve Web geliştirme Iş yüklerinin seçili olduğunu gösteren Visual Studio Yükleyicisi ekran görüntüsü](./media/visual-studio-installer-azure-development.png)

### <a name="authenticate-visual-studio-with-azure"></a>Azure ile Visual Studio kimlik doğrulaması

Visual Studio aracılığıyla uygulamalarda hata ayıklarken, Visual Studio Azure hesabınızı kullanarak kimlik doğrulaması yapabilir ve Azure kaynaklarına erişebilir.  Bu hesap, uygulamaları doğrudan Visual Studio 'dan Azure 'a yayımladığınızda de kullanılır.

Azure hesabınızın kimliğini Visual Studio 'dan doğrulamak için,   >  **Seçenekler** iletişim kutusunu başlatmak üzere Araçlar **Seçenekler** menüsünü seçin. `Azure Service Authentication`Seçeneklere gidin ve Azure hesabınızı kullanarak oturum açın.

![Azure oturum açma bilgilerini gösteren Visual Studio seçenekleri Iletişim kutusunun ekran görüntüsü](./media/visual-studio-azure-login-dialog.png)

### <a name="next-steps"></a>Sonraki adımlar

.NET veya diğer dillerde geliştirme için [Visual Studio Code](https://code.visualstudio.com/) de kullanıyorsanız, [Azure geliştirmesi için Visual Studio Code de yapılandırmanız](./configure-vs-code.md)gerekir. Aksi takdirde, [Azure CLI 'Yı yüklemeye](./install-azure-cli.md)devam edin.
