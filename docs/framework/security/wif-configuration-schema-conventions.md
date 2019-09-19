---
title: WIF Yapılandırma Şeması Kuralları
ms.date: 03/30/2017
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
author: BrucePerlerMS
ms.openlocfilehash: c02d467260a5197cdd01a3819f8a323655a8a08f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045091"
---
# <a name="wif-configuration-schema-conventions"></a>WIF Yapılandırma Şeması Kuralları
Bu konuda, Windows Identity Foundation (WIF) yapılandırma konularında kullanılan kurallar ele alınmaktadır ve [ \<System. IdentityModel](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) [ \< > ve ' de kullanılan bazı ortak özellikler ve öznitelikler açıklanmaktadır. System. IdentityModel. Services >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) bölümler.  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>Mod  
 WIF yapılandırma öğelerinin birçoğu bir `mode` özniteliğe sahiptir. Bu öznitelik, genellikle işlemenin belirli bir parçasını yapmak için kullanılan sınıfı ve geçerli öğenin alt öğeleri olarak hangi yapılandırma öğelerine izin verileceğini denetler. Yapılandırma dosyasına dahil edilen öğeler mod ayarları nedeniyle yoksayılırsa, bir yapılandırma hatası oluşur.  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>TimeSpan değerleri  
 Bir <xref:System.TimeSpan> özniteliğin türü olarak kullanıldığı yer, izin verilen biçimi görmek için <xref:System.TimeSpan.Parse%28System.String%29> yöntemine bakın. Bu biçim aşağıdaki belirtime uyar.  
  
`[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]`  
  
 Örneğin, "30", "30.00:00", "30.00:00:00" tümü 30 gün; ve "00:05", "00:05:00", "0.00:05:00.00" tümü 5 dakikada bir gelir.  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>Sertifika başvuruları  
 Birkaç öğe, `<certificateReference>` öğesini kullanarak sertifikalara başvurular alır. Bir sertifikaya başvurulduğunda, aşağıdaki öznitelikler kullanılabilir.  
  
|||  
|-|-|  
|`storeLocation`|<xref:System.Security.Cryptography.X509Certificates.StoreLocation> Sabit listesinin bir değeri: `CurrentUser` veya `CurrentMachine`.|  
|`storeName`|<xref:System.Security.Cryptography.X509Certificates.StoreName> Sabit listesinin bir değeri; bu bağlam için en yararlı değer ve ' `My` `TrustedPeople`dir.|  
|`x509FindType`|<xref:System.Security.Cryptography.X509Certificates.X509FindType> Sabit listesinin bir değeri; bu bağlam için en yararlı değer ve ' `FindBySubjectName` `FindByThumbprint`dir. Hata olasılığını ortadan kaldırmak için, `FindByThumbprint` türün üretim ortamlarında kullanılması önerilir.|  
|`findValue`|`x509FindType` Özniteliği temel alarak sertifikayı bulmak için kullanılan değer. Hata olasılığını ortadan kaldırmak için, `FindByThumbprint` türün üretim ortamlarında kullanılması önerilir. `FindByThumbPrint` Belirtildiğinde, bu öznitelik, sertifika parmak izinin onaltılı dize biçimi olan bir değer alır; örneğin, "97249e1a5fa6bee5e515b82111ef524a4c91583f".|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>Özel tür başvuruları  
 Birçok öğe özel türlere `type` özniteliği kullanarak başvurur. Bu öznitelik, özel türün adını belirtmelidir. Genel derleme önbelleğinden (GAC) bir türe başvurmak için, tanımlayıcı bir ad kullanılmalıdır. Bin/dizindeki bir derlemeden bir türe başvurmak için, basit bir derleme nitelikli başvuru kullanılabilir. App_Code/Directory içinde tanımlı türlere, yalnızca uygun derleme olmadan tür adı belirtilerek de başvurulabilir.  
  
 Özel türler belirtilen türden türetilmelidir ve `public` varsayılan (0 bağımsız değişken) Oluşturucusu sağlamalıdır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [\<System. IdentityModel >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)
- [\<System. IdentityModel. Services >](../configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
