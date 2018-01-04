---
title: "JSON Web Belirteci İşleyicisi Paketini İndirme"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d12b3f5b-f1f1-4a9d-a159-0c13e5976c90
caps.latest.revision: "3"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5982830404d8d8780bf41153741928b68dc5c7d6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
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
