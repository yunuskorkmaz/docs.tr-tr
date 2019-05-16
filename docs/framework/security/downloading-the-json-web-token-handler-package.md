---
title: JSON Web Belirteci İşleyicisi Paketini İndirme
ms.date: 10/10/2018
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
ms.openlocfilehash: a8685a71d46778d932595965f32c0041b176bd83
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633521"
---
# <a name="download-the-json-web-token-handler-package"></a>JSON Web belirteci işleyicisi paketini indirme

Bu konuda, indirin ve JSON Web belirteci işleyicisi projenizde anlatılmaktadır.

JSON Web belirteci işleyicisi uzantısı, gerekli derlemeleri ve başvuruları projenize ekleyen bir NuGet paketi olarak kullanılabilir. Yüklü olan NuGet zaten yoksa, Git [nuget.org](https://nuget.org) yükleyin. Kendi sayfasını ziyaret ederek uzantının sürüm geçmişini görebilirsiniz: [NuGet üzerinde JSON Web belirteci işleyicisi](https://www.nuget.org/packages/System.IdentityModel.Tokens.Jwt/)

## <a name="use-the-package-manager-gui"></a>Paket Yöneticisi GUI kullanma

1. Visual Studio'da, projenize sağ tıklayın **Çözüm Gezgini**ve ardından **NuGet paketlerini Yönet**.

2. İçinde **NuGet paketlerini Yönet** penceresinde arama kutusuna tıklayın ve girin `JWT Token Handler` basın **Enter**.

3. Sonuçlar bölmesinde, tıklayın **yükleme** düğmesine ilk sonuç.

4. Paketin indirilmesi başlar. Projenize eklenmeden önce lisans kabulü iletişim kutusu görünür. Lisans koşullarını kabul ediyorsanız tıklayın **kabul ediyorum**.

5. Son JSON Web belirteci işleyici derlemeleri indirilir ve projenize eklenir.

## <a name="use-the-package-manager-console"></a>Paket Yöneticisi Konsolu

1. Visual Studio'da **Araçları** > **NuGet Paket Yöneticisi** > **Paket Yöneticisi Konsolu**.

2. **Paket Yöneticisi Konsolu** görünür. Aşağıdaki metni ve enter tuşuna basın **Enter**:

    ```powershell
    Install-Package System.IdentityModel.Tokens.Jwt
    ```

3. Son JSON Web belirteci işleyici derlemeleri indirilir ve projenize eklenir.
