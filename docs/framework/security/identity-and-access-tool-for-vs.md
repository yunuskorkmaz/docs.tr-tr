---
title: Visual Studio 2012 için Kimlik ve Erişim Aracı
ms.date: 03/30/2017
ms.assetid: 87b8f8f2-4074-44fd-9fd6-08278e877390
author: BrucePerlerMS
ms.openlocfilehash: 65d771b87cd3198848ffac387446abb17df18250
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611594"
---
# <a name="identity-and-access-tool-for-visual-studio-2012"></a>Visual Studio 2012 için Kimlik ve Erişim Aracı
Bu konuda, Visual Studio 11 için yeni Kimlik ve Erişim Aracı açıklanmaktadır. Bu araç şu URL'den indirin: <https://go.microsoft.com/fwlink/?LinkID=245849> veya doğrudan Visual Studio 11 uzantılar Yöneticisi'nde "kimlik" için arama yapın.  
  
 Visual Studio 11 için Kimlik ve Erişim Aracı, aşağıdaki önemli özelliklerle birlikte önemli ölçüde basitleştirilmiş bir geliştirme zamanı deneyimi sağlar:  
  
-   Bu yeni araç ile, web uygulamaları proje türlerini kullanarak geliştirme yapabilir ve IIS express'i hedefleyebilirsiniz.  
  
-   Yalnızca koruma paket kimlik doğrulamasının aksine, yeni araçla yerel ana bölge keşif sayfanızı/denetleyicinizi (uygulamanızda kimlik doğrulama deneyimini gerçekleştiren başka bir uç noktası) belirtebilirsiniz; WIF kimliği doğrulanmamış tüm istekleri STS'ye yönlendirmek yerine buraya gidecek şekilde yapılandıracaktır.  
  
-   Araç, hata ayıklama oturumu başlattığınızda yerel makinenizde çalışan bir test Güvenlik Belirteci Hizmeti (STS) içerir. Bu nedenle, uygulamalarınızı test etmek için ihtiyacınız olan talepleri almak üzere artık özel STS projeleri oluşturmanıza ve bunlara ince ayar yapmanıza gerek yoktur. Talep türleri ve değerler tamamen özelleştirilebilir.  
  
-   Ortak ayarları, web.config'i düzenlemek zorunda kalmadan doğrudan aracın kullanıcı arabirimiyle değiştirebilirsiniz.  
  
-   Tek bir ekranda Active Directory Federasyon Hizmetleri (AD FS) 2.0 (veya diğer WS-Federasyon sağlayıcıları) ile federasyon oluşturabilirsiniz.  
  
-   Araç, kullanmak istediğiniz tüm kimlik sağlayıcıları için basit bir onay kutularını listesi ile Windows Azure Access Control Service (ACS) özelliklerini kullanır: Facebook, Google, Live ID, Yahoo!, tüm Openıd sağlayıcılar ve tüm WS-Federasyon sağlayıcıları. Kimlik sağlayıcılarınızı seçin, Tamam'a tıklayın ve F5'e basın; hem uygulamanız hem de ACS otomatik olarak yapılandırılacak ve test uygulamanız ACS'yi kullanacaktır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [WIF Özellikleri](../../../docs/framework/security/wif-features.md)
