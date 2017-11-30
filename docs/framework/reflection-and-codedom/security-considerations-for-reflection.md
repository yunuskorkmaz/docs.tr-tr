---
title: "Yansımayla İlgili Güvenlik Konuları"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- permissions [.NET Framework], reflection
- MethodInfo parameters
- reflection, security
- partial trust,reflection
- nonpublic members
- reflection,partial trust
- link demands
ms.assetid: 42d9dc2a-8fcc-4ff3-b002-4ff260ef3dc5
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 756873e93d6e13cbb9077d10a52a718932afcedb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="security-considerations-for-reflection"></a>Yansımayla İlgili Güvenlik Konuları
Yansıma erişim üyeleri ve bu türleri ve üyeleri hakkında bilgi alma özelliği sağlar (diğer bir deyişle, yöntemleri ve almak ve özelliği ayarlamak için oluşturucular çağırmak için değerleri, ekleme ve olay işleyicileri kaldırın ve benzeri). Türleri ve üyeleri hakkında bilgi edinmek için yansıma kullanımını sınırlı değildir. Tüm kod yansıma aşağıdaki görevleri gerçekleştirmek için kullanabilirsiniz:  
  
-   Numaralandırma türleri ve üyeleri ve bunların meta verilerini inceleyin.  
  
-   Numaralandırma ve derlemeler ve modüller inceleyin.  
  
 Yansıma erişim üyelerine, buna karşın sınırlamalara tabidir kullanmaktır. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], yalnızca güvenilen kod güvenlik kritik üyelere erişmek için yansıma kullanabilir. Ayrıca, yalnızca güvenilen kod yansıma derlenmiş kod doğrudan erişilebilir olmaz ortak olmayan üyeler erişmek için kullanabilirsiniz. Son olarak, güvenli kritik üyesi erişmek için yansıma kullanan kodu olarak derlenmiş kod ile yalnızca güvenli kritik üye taleplerini ne olursa olsun izinlerine sahip olmalıdır.  
  
 Gerekli izinleri tabi kodu yansıma erişimi şu tür gerçekleştirmek için kullanabilirsiniz:  
  
-   Güvenlik açısından kritik olmayan erişim Genel üyeler.  
  
-   İçin erişilebilir olan erişim ortak olmayan üyeler derlenmiş kod, bu üyeler güvenlik açısından kritik değilse. Bu tür ortak olmayan üyeler örnekleri şunlardır:  
  
    -   Arama kodun temel sınıflarının üyelerini korumalı. (Yansıma, bu için ailesi düzeyinde erişim adlandırılır.)  
  
    -   `internal`Üyeler (`Friend` üyeleri Visual Basic'te) arama kodun derlemesindeki. (Yansıma, bu için derleme düzeyinde erişim adlandırılır.)  
  
    -   Özel üyelerin diğer örneklerinin çağıran kodu içeren sınıf.  
  
 Uygulama etki alanı ek izinler verir sürece Örneğin, bir korumalı uygulama etki alanında çalışan kod bu listede açıklanan erişim sınırlıdır.  
  
 İle başlayarak [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], normalde erişilemeyen üyeleri erişmeye artı hedef nesnenin verme kümesi için bir talep oluşturur <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağı. Tam güven (örneğin, komut satırından başlatıldığında bir uygulama kodunda) ile çalışan kodu her zaman bu izinleri karşılayabilen. (Bu güvenlik açısından kritik üyeleri, erişim kısıtlamaları bu makalenin sonraki bölümlerinde açıklandığı gibi tabidir.)  
  
 İsteğe bağlı olarak, bir korumalı uygulama etki alanı verebilirsiniz <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bölümde açıklandığı gibi bayrak [erişme üyeleri emin olduğunuz normalde erişilemez](#accessingNormallyInaccessible), bu makalenin ilerisinde yer.  
  
<a name="accessingSecurityCritical"></a>   
## <a name="accessing-security-critical-members"></a>Güvenlik açısından kritik üyelere erişme  
 Üye güvenlik varsa kritik <xref:System.Security.SecurityCriticalAttribute>, sahip türüne aitse <xref:System.Security.SecurityCriticalAttribute>, ya da güvenlik açısından kritik bir derlemede ise. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], güvenlik açısından kritik üyelere erişme kuralları aşağıdaki gibidir:  
  
-   Kodu tam olarak güvenilmeyen olsa bile saydam kod güvenlik kritik üyelere erişmek için yansıma kullanamazsınız. A <xref:System.MethodAccessException>, <xref:System.FieldAccessException>, veya <xref:System.TypeAccessException> atılır.  
  
-   Kısmi güven ile çalışan kod saydam olarak kabul edilir.  
  
 Güvenlik açısından kritik üyesi doğrudan derlenmiş kod tarafından erişilen veya yansıma kullanarak erişilen bu kurallar aynıdır.  
  
 Komut satırından çalıştırma uygulama kodu tam güven ile çalışır. Saydam olarak işaretlenmemiş sürece bunu yansıma güvenlik açısından kritik üyelere erişmek için kullanabilirsiniz. Aynı kodu kısmi güvende (örneğin, bir korumalı uygulama etki alanı) ile derlemenin güven düzeyi, güvenlik açısından kritik kod erişip erişemeyeceğini belirler çalıştırıldığında: derlemeyi tanımlayıcı ad varsa ve genel derleme önbelleğinde yüklü olduğu bir Güvenilen derleme ve güvenlik açısından kritik üyeleri çağırabilirsiniz. Güvenilir değilse, saydam olarak işaretlenmedi ve güvenlik açısından kritik üyeleri erişemiyor karşın saydam olur.  
  
 Güvenlik modeli hakkında daha fazla bilgi için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
## <a name="reflection-and-transparency"></a>Yansıma ve saydamlık  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], ortak dil çalışma zamanı tür veya derleme güven düzeyi ve uygulama etki alanı güven düzeyini de dahil olmak üzere, birkaç etkene üyeden saydamlık düzeyini belirler. Yansıma sağlar <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Type.IsSecuritySafeCritical%2A>, ve <xref:System.Type.IsSecurityTransparent%2A> bir tür saydamlık düzeyi bulmanızı etkinleştirmek için özellikleri. Aşağıdaki tabloda bu özelliklerin geçerli birleşimlerini gösterir.  
  
|Güvenlik düzeyi|IsSecurityCritical|IsSecuritySafeCritical|IsSecurityTransparent|  
|--------------------|------------------------|----------------------------|---------------------------|  
|Kritik|`true`|`false`|`false`|  
|Güvenli kritik|`true`|`true`|`false`|  
|Geçirgen|`false`|`false`|`true`|  
  
 Bu özellikleri kullanarak bir derlemeyi ve türlerinden güvenlik ek açıklamaları inceleyerek, geçerli güven düzeyi denetimi ve zamanının kuralları oluşturmaya çalışırken daha çok daha kolaydır. Örneğin, bir korumalı uygulama etki alanı çalıştırdığınızda aynı türde güvenlik açısından kritik komut satırından çalıştırıldığında veya güvenlik saydam olabilir.  
  
 Benzer özellikleri vardır <xref:System.Reflection.MethodBase>, <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.Emit.TypeBuilder>, <xref:System.Reflection.Emit.MethodBuilder>, ve <xref:System.Reflection.Emit.DynamicMethod> sınıfları. (Soyutlamalar diğer yansıma ve yansıma yayma, güvenlik öznitelikleri uygulanan ilişkili yöntemleri; Örneğin, özellik erişimcisi uygulanan özellikler durumunda.)  
  
<a name="accessingNormallyInaccessible"></a>   
## <a name="accessing-members-that-are-normally-inaccessible"></a>Normalde erişilemeyen üyelere erişme  
 Ortak dil çalışma zamanı erişilebilirlik kurallarına göre erişilemeyen üyeleri çağrılacak yansıma kullanmak için kodunuzu iki izinlerden biri verilmesi gerekir:  
  
-   Ortak olmayan herhangi bir üyenin çağırmak kodu izin vermek için: kodunuzu verilmelidir <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağı.  
  
    > [!NOTE]
    >  Varsayılan olarak, güvenlik ilkesi Internet'ten kaynaklı kod bu izni reddeder. Bu izni hiçbir zaman Internet'ten kaynaklı kod verilmelidir.  
  
-   Çağrılan üyeyi içeren derlemenin grant kümesi ile aynı olduğu sürece herhangi bir ortak olmayan üyesi çağırmak için kodu veya bir alt kümesini, verme kümesi izin verecek şekilde çağırma içeren bütünleştirilmiş kod: kodunuzu verilmelidir <xref:System.Security.Permissions.ReflectionPermission> ile<xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType>bayrağı.  
  
 Örneğin, Internet izinleri artı uygulama etki alanı verin varsayalım <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrak ve ardından iki derlemelerle A ve b Internet uygulamasını çalıştırın  
  
-   Derlemenin B grant kümesi A değil verilmiş tüm izinleri içermediğinden derlemesi yansıma derleme B, özel üyelerine erişmek için kullanabilirsiniz.  
  
-   Derlemesi özel üyelerine erişmek için yansıma kullanamazsınız [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] derlemeler mscorlib.dll gibi mscorlib.dll tam olarak güvenilmeyen ve bu nedenle A. derlemeye verilmemiş izinlere sahip olduğundan A <xref:System.MemberAccessException> kod erişim güvenliği yığın çalışma zamanında anlatılmaktadır zaman oluşturulur.  
  
## <a name="serialization"></a>Serileştirme  
 Seri hale getirme, <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A?displayProperty=nameWithType> bayrağını alma ve erişilebilirlik bağımsız olarak seri hale getirilebilir türler üyeleri ayarlama olanağı sağlar. Bu izni bulmak ve bir örneğinin özel durumu değiştirmek kod sağlar. (Uygun izinleri verilmeden yanı sıra türü olmalıdır [işaretlenmiş](../../../docs/standard/attributes/applying-attributes.md) meta verilerde serileştirilebilir.)  
  
## <a name="parameters-of-type-methodinfo"></a>Türü MethodInfo parametreleri  
 Genel üyeler Süren yazılmasını engellemek <xref:System.Reflection.MethodInfo> , özellikle Güvenilen kod parametreleri. Bu tür üyeler için kötü amaçlı kod daha savunmasız olabilir. Örneğin, ortak bir üye alan yüksek derecede güvenilen kodda düşünün bir <xref:System.Reflection.MethodInfo> parametresi. Ortak üye dolaylı olarak çağırır varsayın <xref:System.Reflection.MethodBase.Invoke%2A> sağlanan parametre yöntemi. Ortak üye çağrısı gerekli izin denetimleri yapmıyorsa <xref:System.Reflection.MethodBase.Invoke%2A> yöntemi her zaman başarılı olur, çünkü güvenlik sistemi çağıran yüksek oranda güvenilir olduğunu belirler. Kötü amaçlı kod doğrudan yöntemini çağırmak için izni yok olsa bile, yine şekilde dolaylı olarak ortak üye çağırarak bunu yapabilirsiniz.  
  
## <a name="version-information"></a>Sürüm Bilgileri  
  
-   İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], saydam kod güvenlik kritik üyelere erişmek için yansıma kullanamazsınız.  
  
-   <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> Bayrağı içinde sunulan [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)]. ' In önceki sürümlerini [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] gerektiren <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> ortak olmayan üyeler erişmek için yansıma kullanan kodu için bayrak. Kısmen güvenilen kod verilen hiçbir zaman izin budur.  
  
-   İle başlayarak [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], ortak olmayan türleri ve üyeleri hakkında bilgi edinmek için yansıma kullanarak tüm izinleri gerektirmez. Önceki sürümlerde, <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> bayrağı gereklidir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Security.Permissions.ReflectionPermissionFlag>  
 <xref:System.Security.Permissions.ReflectionPermission>  
 <xref:System.Security.Permissions.SecurityPermission>  
 [Güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md)  
 [Kod erişimi güvenliği](../../../docs/framework/misc/code-access-security.md)  
 [Güvenlik sorunları yansıma yayma](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)  
 [Tür bilgilerini görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [Öznitelikleri uygulama](../../../docs/standard/attributes/applying-attributes.md)  
 [Özel özniteliklere erişme](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)
