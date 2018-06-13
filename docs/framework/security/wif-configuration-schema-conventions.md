---
title: WIF yapılandırma şeması kuralları
ms.date: 03/30/2017
ms.assetid: f7864356-f72f-4cae-995c-18e0431f8a58
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 3109b75ccf9cefcad4e112cca02e932ea5489d24
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410409"
---
# <a name="wif-configuration-schema-conventions"></a>WIF yapılandırma şeması kuralları
Bu konu Windows Identity Foundation (WIF) yapılandırma konuları kullanılan kuralları açıklar ve bazı ortak özelliklerini açıklar ve kullanılan öznitelikler [ \<System.IdentityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md) ve [ \<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md) bölümler.  
  
<a name="BKMK_Modes"></a>   
## <a name="modes"></a>Modları  
 Çoğu WIF yapılandırma öğelerinin bir `mode` özniteliği. Bu öznitelik, hangi sınıfın belirli bir işleme parçası yapmak için kullanılır ve hangi yapılandırma öğelerinin geçerli öğenin alt öğeleri izin verilen genellikle denetler. Bir yapılandırma hatası nedeniyle modu ayarlarını yapılandırma dosyasında bulunan öğeleri göz ardı gerekiyorsa gerçekleştirilecektir.  
  
<a name="BKMK_TimespanValues"></a>   
## <a name="timespan-values"></a>TimeSpan değerleri  
 Burada <xref:System.TimeSpan> olan bir öznitelik türü olarak kullanıldığında, bkz: <xref:System.TimeSpan.Parse%28System.String%29> izin verilen biçim görmek için yöntem. Bu biçim aşağıdaki belirtimlerine uygun.  
  
```  
[ws][-]{ d | [d.]hh:mm[:ss[.ff]] }[ws]  
```  
  
 Örneğin, "30", "30.00:00", "30.00:00:00" tüm 30 gün anlamına gelmektedir. ve "00:05", "00: 05:00", "0.00:05:00.00" tüm 5 dakika anlamına gelir.  
  
<a name="BKMK_CertificateReferences"></a>   
## <a name="certificate-references"></a>Sertifika başvuruları  
 Çeşitli öğeleri kullanarak sertifikaları başvurular ele `<certificateReference>` öğesi. Aşağıdaki öznitelikler, bir sertifika başvururken kullanılabilir.  
  
|||  
|-|-|  
|`storeLocation`|Değerini <xref:System.Security.Cryptography.X509Certificates.StoreLocation> numaralandırma: `CurrentUser` veya `CurrentMachine`.|  
|`storeName`|Değerini <xref:System.Security.Cryptography.X509Certificates.StoreName> numaralandırma; en yararlı bu bağlam için olan `My` ve `TrustedPeople`.|  
|`x509FindType`|Değerini <xref:System.Security.Cryptography.X509Certificates.X509FindType> numaralandırma; en yararlı bu bağlam için olan `FindBySubjectName` ve `FindByThumbprint`. Hata olasılığını ortadan kaldırmak için önerilir `FindByThumbprint` türü üretim ortamlarında kullanılabilir.|  
|`findValue`|Sertifikayı bulmak için kullanılan değer temel alarak `x509FindType` özniteliği. Hata olasılığını ortadan kaldırmak için önerilir `FindByThumbprint` türü üretim ortamlarında kullanılabilir. Zaman `FindByThumbPrint` belirtilirse, bu öznitelik sertifika onaltılık dize biçiminde olan bir değer alır parmak izi; Örneğin, "97249e1a5fa6bee5e515b82111ef524a4c91583f".|  
  
<a name="BKMK_CustomTypeReferences"></a>   
## <a name="custom-type-references"></a>Özel tür başvuruları  
 Çeşitli öğeleri kullanarak özel türler başvurusu `type` özniteliği. Bu öznitelik özel türünün adı belirtmeniz gerekir. Genel Derleme Önbelleği (GAC) bir türü başvurmak için güçlü bir ad kullanılmalıdır. Depo derlemedeki bir türe başvuruda için / dizinini, basit bir bütünleştirilmiş kod tam başvuru kullanılabilir. App_Code içinde tanımlı türler / dizini de yalnızca belirleme derleme ile tür adı belirterek başvurulabilir.  
  
 Özel türler belirtilen türünden türetilmelidir ve sağlamaları gerekir bir `public` varsayılan (0 bağımsız değişkeni) Oluşturucu.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [\<System.IdentityModel >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)  
 [\<system.identityModel.services >](../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)
