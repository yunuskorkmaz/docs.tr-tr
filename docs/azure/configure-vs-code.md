---
title: .NET ile Azure geliştirme için Visual Studio Code yapılandırma
description: Bu makale, VS Code ' de yüklü ve yapılandırılmış doğru eklentilerin alınması dahil olmak üzere Azure geliştirme için Visual Studio Code yapılandırmanıza yardımcı olur
ms.date: 11/30/2020
ms.topic: conceptual
ms.custom: devx-track-dotnet
ms.author: daberry
author: daberry
ms.openlocfilehash: 65ced99befe12d137062b4ea6a59a1ccd3099e0b
ms.sourcegitcommit: 3d6d6595a03915f617349781f455f838a44b0f44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/19/2020
ms.locfileid: "97701214"
---
# <a name="configure-visual-studio-code-for-azure-development"></a>Azure geliştirme için Visual Studio Code yapılandırma

.NET geliştirmesi için Visual Studio Code kullanıyorsanız, angular, yanıt verme veya Vue gibi çerçeveleri kullanarak tek sayfalı uygulamalar oluşturmaya veya Python gibi başka bir dilde uygulama yazmaya yönelik olarak Azure geliştirme için Visual Studio Code yapılandırmak isteyeceksiniz.

### <a name="download-visual-studio-code"></a>Visual Studio Code'u indirin

Zaten Visual Studio Code yüklüyse, bu adımı atlayabilirsiniz

> [!div class="nextstepaction"]
> [Visual Studio Code'u indirin](https://code.visualstudio.com/download)

### <a name="install-the-azure-tools-extension-pack"></a>Azure araçları uzantı paketini yükler

[Azure araçları uzantı paketi](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) , tek bir kullanışlı pakette Azure App Service, Azure Işlevleri, Azure depolama, Cosmos DB ve Azure sanal makineleri ile çalışmaya yönelik uzantılar içerir.

Uzantıyı Visual Studio Code yüklemek için:

1. **Uzantılar** penceresini açmak için <kbd>CTRL + SHIFT + X</kbd> tuşlarına basın.
1. *Azure Araçları* uzantısını arayın.
1. **Install** düğmesini seçin.

![Azure araçları uzantı paketi için arama uzantıları paneli 'ni gösteren Visual Studio Code ekran görüntüsü](./media/visual-studio-code-azure-tools.png)

Visual Studio Code Uzantıları yükleme hakkında daha fazla bilgi edinmek için Visual Studio Code Web sitesindeki [uzantı marketi](https://code.visualstudio.com/docs/editor/extension-gallery) belgesine bakın.

### <a name="sign-in-to-your-azure-account-with-azure-tools"></a>Azure Araçları 'nı kullanarak Azure hesabınızda oturum açın

Sol bölmede bir Azure simgesi görürsünüz. Bu simgeyi seçin ve Azure hizmetleri için bir denetim masası görüntülenir. Visual Studio Code ' deki Azure Araçları için kimlik doğrulama işlemini tamamlamaya yönelik herhangi bir hizmette **Azure... oturum aç '** ı seçin.

![Azure araçlarının Azure 'da nasıl oturum açışını gösteren Visual Studio Code ekran görüntüsü](./media/visual-studio-code-azure-login.png)

### <a name="next-steps"></a>Sonraki adımlar

Daha sonra, Azure CLı 'yi iş istasyonunuza yüklemek isteyeceksiniz.

> [!div class="nextstepaction"]
> [Azure CLI'yi yükleme](./install-azure-cli.md)
