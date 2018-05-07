---
title: JSON Web Belirteci İşleyicisi Paketini İndirme
ms.date: 03/30/2017
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: 5a4846a5ec92324105f41b320d0d77f8749c28f9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="downloading-the-json-web-token-handler-package"></a>JSON Web Belirteci İşleyicisi Paketini İndirme
Bu konu, indirin ve JSON Web belirteci işleyicisi projenizde nasıl kullanılacağını açıklar.  
  
## <a name="downloading-the-json-web-token-handler"></a>JSON Web Belirteci İşleyicisini İndirme  
 JSON Web belirteci işleyicisi uzantısı gerekli derlemeler ve başvuruları projenize ekler bir NuGet paketi olarak kullanılabilir. Yüklü NuGet zaten yoksa, Git [nuget.org](http://nuget.org) yükleyin. NuGet üzerinde kendi sayfasını ziyaret ederek uzantısı sürüm geçmişini görebilirsiniz: [NuGet üzerinde JSON Web belirteci işleyicisi](http://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-gui"></a>Paket Yöneticisi GUI'sini kullanarak JSON Web belirteci işleyicisi indirme  
  
1.  Visual Studio'da, projenize sağ **Çözüm Gezgini**ve ardından **NuGet paketlerini Yönet**.  
  
2.  İçinde **NuGet paketlerini Yönet** penceresinde arama kutusuna tıklayın ve girin `JWT Token Handler` ve basın **Enter**.  
  
3.  Sonuçlar bölmesinde, tıklatın **yüklemek** ilk sonucu düğmesi.  
  
4.  Paket, karşıdan yükleme başlar. Projenize eklenmeden önce lisans kabulünü iletişim kutusu görüntülenir. Lisans koşullarını kabul ediyorsa **kabul ediyorum**.  
  
5.  En son JSON Web belirteci işleyicisi derlemeler indirilir ve projenize eklenir.  
  
#### <a name="downloading-the-json-web-token-handler-by-using-the-package-manager-console"></a>Paket Yöneticisi konsolu kullanılarak JSON Web belirteci işleyicisi indirme  
  
1.  Visual Studio'da sırasıyla **Araçları**, **kitaplık Paket Yöneticisi**ve ardından **Paket Yöneticisi Konsolu**.  
  
2.  **Paket Yöneticisi Konsolu** görüntülenir. Aşağıdaki metin ve ENTER tuşuna basın **Enter**:  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.Jwt  
    ```  
  
3.  En son JSON Web belirteci işleyicisi derlemeler indirilir ve projenize eklenir.
