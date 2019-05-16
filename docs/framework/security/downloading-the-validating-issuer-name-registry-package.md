---
title: Yayınlayıcı Adı Kaydı Paketini Doğrulamayı İndirme
ms.date: 10/10/2018
ms.assetid: ff8b0014-c5d4-4614-90f0-13fcc0ba777a
ms.openlocfilehash: 5684844f1db33b075df099b3026d9d0c1061199f
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631841"
---
# <a name="download-the-validating-issuer-name-registry-package"></a>Doğrulama verenin adı kaydı paketini indirme

Bu konuda, indirin ve doğrulama verenin ad kayıt defteri (VINR) projenizde anlatılmaktadır.

VINR, gerekli derlemeleri ve başvuruları projenize ekleyen bir NuGet paketi olarak kullanılabilir. Yüklü olan NuGet zaten yoksa, Git [nuget.org](https://nuget.org) yükleyin. Kendi sayfasını ziyaret ederek uzantının sürüm geçmişini görebilirsiniz: [Microsoft NuGet üzerindeki yayınlayıcı adı kaydını doğrulama](https://nuget.org/packages/System.IdentityModel.Tokens.ValidatingIssuerNameRegistry/)

## <a name="use-the-package-manager-gui"></a>Paket Yöneticisi GUI kullanma

1. Visual Studio'da, projenize sağ tıklayın **Çözüm Gezgini**ve ardından **NuGet paketlerini Yönet**.

2. İçinde **NuGet paketlerini Yönet** penceresinde arama kutusuna tıklayın ve girin `ValidatingIssuerNameRegistry` basın **Enter**.

3. Sonuçlar bölmesinde, tıklayın **yükleme** düğmesine ilk sonuç.

4. Paketin indirilmesi başlar. Projenize eklenmeden önce lisans kabulü iletişim kutusu görünür. Lisans koşullarını kabul ediyorsanız tıklayın **kabul ediyorum**.

5. Son VINR derlemeleri indirilir ve projenize eklenir.

## <a name="use-the-package-manager-console"></a>Paket Yöneticisi Konsolu

1. Visual Studio'da **Araçları** > **NuGet Paket Yöneticisi** > **Paket Yöneticisi Konsolu**.

2. **Paket Yöneticisi Konsolu** görünür. Aşağıdaki metni ve enter tuşuna basın **Enter**:

    ```powershell
    Install-Package System.IdentityModel.Tokens.ValidatingIssuerNameRegistry
    ```

3. Son VINR derlemeleri indirilir ve projenize eklenir.
