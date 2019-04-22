---
title: WIF Yapılandırma Şeması Kuralları
ms.date: 03/30/2017
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
author: BrucePerlerMS
ms.openlocfilehash: 39ed32bb7e926f275e996b09e746c879c6d3fe9e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120880"
---
# <a name="wif-configuration-schema-conventions"></a>WIF Yapılandırma Şeması Kuralları
Bu konu, Windows Identity Foundation (WIF) yapılandırma konuları kullanılan kuralları açıklar ve bazı ortak özelliklerini açıklar ve kullanılan öznitelikler [ \<system.identityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) ve [ \<System.IdentityModel.Services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) bölümler.  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>Modları  
 WIF yapılandırma öğelerinin çoğu bir `mode` özniteliği. Bu öznitelik genellikle hangi sınıfın belirli bir işleme parçası yapmak için kullanılır ve hangi yapılandırma öğelerinin geçerli öğenin alt öğeleri izin verilir denetimleri. Bir yapılandırma hatası nedeniyle modu ayarları yapılandırma dosyasında bulunan öğeleri göz ardı edilir gerçekleştirilecektir.  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>TimeSpan değerleri  
 Burada <xref:System.TimeSpan> olan bir öznitelik türü kullanıldığında, bkz: <xref:System.TimeSpan.Parse%28System.String%29> izin verilen biçim görmek için yöntemi. Bu biçim için şu belirtime uygun.  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 Örneğin, "30", "30.00:00", "30.00:00:00" tüm 30 gün anlamına gelmektedir. ve "00:05", "00: 05:00", "0.00:05:00.00" tüm 5 dakika anlamına gelir.  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>Sertifika başvuruları  
 Sertifikaları kullanarak başvurular çeşitli öğeler ele `<certificateReference>` öğesi. Bir sertifika başvururken aşağıdaki öznitelikleri kullanılabilir.  
  
|||  
|-|-|  
|`storeLocation`|Değerini <xref:System.Security.Cryptography.X509Certificates.StoreLocation> numaralandırma: `CurrentUser` veya `CurrentMachine`.|  
|`storeName`|Değerini <xref:System.Security.Cryptography.X509Certificates.StoreName> numaralandırma; en yararlı olan bu bağlam için `My` ve `TrustedPeople`.|  
|`x509FindType`|Değerini <xref:System.Security.Cryptography.X509Certificates.X509FindType> numaralandırma; en yararlı olan bu bağlam için `FindBySubjectName` ve `FindByThumbprint`. Hata olasılığını ortadan kaldırmak için önerilir `FindByThumbprint` türü, üretim ortamlarında kullanılabilir.|  
|`findValue`|Sertifika bulmak için kullanılan değerini temel alarak `x509FindType` özniteliği. Hata olasılığını ortadan kaldırmak için önerilir `FindByThumbprint` türü, üretim ortamlarında kullanılabilir. Zaman `FindByThumbPrint` belirtilirse, bu öznitelik sertifika onaltılık dize biçiminde bir değer alır parmak izi; Örneğin, "97249e1a5fa6bee5e515b82111ef524a4c91583f".|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>Özel tür başvuruları  
 Çeşitli öğeleri kullanarak özel türler başvurusu `type` özniteliği. Bu öznitelik, özel bir tür adını belirtmeniz gerekir. Genel Derleme Önbelleği (GAC) gelen bir tür başvuru için bir tanımlayıcı ad kullanılmalıdır. Depo bir derlemeden bir tür başvurmak için / dizin, bir basit başvuru bütünleştirilmiş kodla nitelenen kullanılabilir. App_Code içinde tanımlı türleri / dizin ile uygun bir derleme yok basit tür adı belirterek de başvurulabilir.  
  
 Özel türler belirtilen türden türetilmiş ve sağlamaları gerekir bir `public` varsayılan (0 bağımsız değişkeni) Oluşturucu.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<System.IdentityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)
- [\<System.IdentityModel.Services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
