---
title: Yayınlayıcı Adı Kaydı Paketini Doğrulamayı İndirme
ms.date: 03/30/2017
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 03b68f4b9dc6fde02c951968067e0311e4981d33
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33398755"
---
# <a name="downloading-the-validating-issuer-name-registry-package"></a>Yayınlayıcı Adı Kaydı Paketini Doğrulamayı İndirme
Bu konu, indirin ve doğrulama verenin adı kayıt defteri (VINR) projenizde nasıl kullanılacağını açıklar.  
  
## <a name="downloading-the-validating-issuer-name-registry"></a>Doğrulama yayınlayıcı adı kaydını indirme  
 VINR gerekli derlemeler ve başvuruları projenize ekler bir NuGet paketi olarak kullanılabilir. Yüklü NuGet zaten yoksa, Git [nuget.org](http://nuget.org) yükleyin. NuGet üzerinde kendi sayfasını ziyaret ederek uzantısı sürüm geçmişini görebilirsiniz: [Microsoft doğrulama yayınlayıcı adı kaydını NuGet üzerinde](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-gui"></a>Paket Yöneticisi GUI'sini kullanarak doğrulama yayınlayıcı adı kaydını indirme  
  
1.  Visual Studio'da, projenize sağ **Çözüm Gezgini**ve ardından **NuGet paketlerini Yönet**.  
  
2.  İçinde **NuGet paketlerini Yönet** penceresinde arama kutusuna tıklayın ve girin `ValidatingIssuerNameRegistry` ve basın **Enter**.  
  
3.  Sonuçlar bölmesinde, tıklatın **yüklemek** ilk sonucu düğmesi.  
  
4.  Paket, karşıdan yükleme başlar. Projenize eklenmeden önce lisans kabulünü iletişim kutusu görüntülenir. Lisans koşullarını kabul ediyorsa **kabul ediyorum**.  
  
5.  En son VINR derlemeler indirilir ve projenize eklenir.  
  
#### <a name="downloading-the-validating-issuer-name-registry-by-using-the-package-manager-console"></a>Paket Yöneticisi konsolunu kullanarak doğrulama yayınlayıcı adı kaydını indirme  
  
1.  Visual Studio'da sırasıyla **Araçları**, **kitaplık Paket Yöneticisi**ve ardından **Paket Yöneticisi Konsolu**.  
  
2.  **Paket Yöneticisi Konsolu** görüntülenir. Aşağıdaki metin ve ENTER tuşuna basın **Enter**:  
  
    ```powershell  
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry  
    ```  
  
3.  En son VINR derlemeler indirilir ve projenize eklenir.
