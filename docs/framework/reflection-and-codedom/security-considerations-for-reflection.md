---
title: Yansımayla İlgili Güvenlik Konuları
ms.date: 03/30/2017
helpviewer_keywords:
- permissions [.NET Framework], reflection
- MethodInfo parameters
- reflection, security
- partial trust,reflection
- nonpublic members
- reflection,partial trust
- link demands
ms.assetid: 42d9dc2a-8fcc-4ff3-b002-4ff260ef3dc5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8c238f0aebd7c81443eb55fe0ee84844f0c9aee8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207519"
---
# <a name="security-considerations-for-reflection"></a>Yansımayla İlgili Güvenlik Konuları
Yansıma üyelerine erişmek ve bu türler ve üyeler hakkında bilgi alma özelliği sağlar (diğer bir deyişle, yöntemler ve almak ve özellik ayarlamak için oluşturucuları çağırmak için değerleri, ekleyin ve olay işleyicilerini kaldırmak ve benzeri). Türler ve üyeler hakkında bilgi edinmek için yansıma kullanmak sınırlı değildir. Tüm kod, yansıma aşağıdaki görevleri gerçekleştirmek için kullanabilirsiniz:  
  
-   Türleri ve üyeleri listeleme ve meta verilerinin inceleyin.  
  
-   Listeleme ve derlemeler ve modüller inceleyin.  
  
 Üyelerine erişmek için yansıma kullanmak, aksine, sınırlamalara tabi olabilir. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], yalnızca güvenilen kod güvenlik kritik üyelere erişim için yansıma kullanabilir. Ayrıca, yalnızca güvenilen kod, yansıma derlenmiş kodu doğrudan erişilebilir olmaz ortak olmayan üyelere erişmek için kullanabilirsiniz. Son olarak, güvenli kritik bir üyesine erişmek için yansımayı kullanan kod ile derlenmiş kodu olarak yalnızca güvenli kritik üye taleplerini izinlere olmalıdır.  
  
 Gerekli izinleri tabi kodu yansıma erişimi şu tür gerçekleştirmek için kullanabilirsiniz:  
  
-   Güvenlik açısından kritik olmayan erişim Genel üyeler.  
  
-   Bu üyelere güvenlik açısından kritik değilse, derlenmiş kod, erişilebilir olabilecek erişim ortak olmayan üyeler. Böyle bir ortak olmayan üyeler örnekleri şunlardır:  
  
    -   Çağıran kodun temel sınıflar korumalı üyeleri. (Yansıma, bu aile düzeyinde erişim adlandırılır.)  
  
    -   `internal` Üyeler (`Friend` üyeleri Visual Basic'te) çağıran kodun derlemesi içindeki. (Yansıma, bu derleme düzeyinde erişim adlandırılır.)  
  
    -   Özel üyeler, diğer örneklerin çağıran kod içeren sınıf.  
  
 Sürece, uygulama etki alanı ek izinler verir. Örneğin, bir koruma alanlı uygulama etki alanında çalışmasını kod bu listede tanımlanan erişim sınırlıdır.  
  
 İle başlayarak [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)], normalde erişilemeyen üyeler erişmeye artı hedef nesnenin izin kümesi için bir talep oluşturur <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağı. Tam güven (örneğin, komut satırından başlatıldığında bir uygulamadaki kodu) ile çalışan kodu her zaman bu izinleri karşılayabilecek. (Güvenlik açısından kritik üyeleri erişimde sınırlamalar bu makalenin sonraki bölümlerinde açıklandığı gibi budur.)  
  
 İsteğe bağlı olarak, koruma alanlı uygulama etki alanı verebilirsiniz <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bölümünde açıklandığı gibi bayrak [erişme üyeleri emin olan normalde erişilemez](#accessingNormallyInaccessible), bu makalenin ilerleyen bölümlerinde.  
  
<a name="accessingSecurityCritical"></a>   
## <a name="accessing-security-critical-members"></a>Güvenlik açısından kritik üyelerine erişme  
 Üye güvenlik varsa kritik <xref:System.Security.SecurityCriticalAttribute>, olan bir türe ait <xref:System.Security.SecurityCriticalAttribute>, ya da güvenlik açısından kritik bir derlemede ise. İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], güvenlik açısından kritik üyelere erişim için kuralları aşağıdaki gibidir:  
  
-   Tam olarak güvenilen olsa bile saydam kod güvenlik kritik üyelere erişim için yansıma kullanamazsınız. A <xref:System.MethodAccessException>, <xref:System.FieldAccessException>, veya <xref:System.TypeAccessException> oluşturulur.  
  
-   Kısmi güven ile çalışan kodu, saydam olarak kabul edilir.  
  
 Güvenlik açısından kritik üyesi doğrudan derlenmiş kod tarafından erişilen veya yansıma kullanılarak erişilen bu kurallar aynıdır.  
  
 Komut satırından çalışan uygulama kodu, tam güven ile çalışır. Saydam olarak işaretlenmemiş sürece, güvenlik açısından kritik üyelere erişim için yansıma kullanabilirsiniz. (Örneğin, bir koruma alanlı uygulama etki alanında) kısmi güven ile aynı kodu çalıştırdığınızda derlemenin güven düzeyine güvenlik açısından kritik kod erişip erişemeyeceğini belirler: Derleme tanımlayıcı bir ada sahip ve genel derleme önbelleğinde yüklü ise güvenilen bir derleme olduğundan ve güvenlik açısından kritik üyelerini çağırabilirsiniz. Güvenilir değilse, saydam olarak işaretlenmedi ve güvenlik açısından kritik üyeleri erişemiyor karşın saydam olur.  
  
 Güvenlik modeli hakkında daha fazla bilgi için [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], bkz: [güvenlik değişiklikleri](../../../docs/framework/security/security-changes.md).  
  
## <a name="reflection-and-transparency"></a>Yansıma ve geçirgenlik  
 İle başlayarak [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], ortak dil çalışma zamanı bir türün veya derlemenin güven düzeyine ve uygulama etki alanının güven düzeyi gibi çeşitli unsurlardan üyeden saydamlık düzeyini belirler. Yansıma sağlar <xref:System.Type.IsSecurityCritical%2A>, <xref:System.Type.IsSecuritySafeCritical%2A>, ve <xref:System.Type.IsSecurityTransparent%2A> sağlamak saydamlık düzeyi bir tür bulmak özellikleri. Bu özelliklerin geçerli birleşimleri aşağıdaki tabloda gösterilmektedir.  
  
|Güvenlik düzeyi|IsSecurityCritical|IsSecuritySafeCritical|IsSecurityTransparent|  
|--------------------|------------------------|----------------------------|---------------------------|  
|Kritik|`true`|`false`|`false`|  
|Güvenli-kritik|`true`|`true`|`false`|  
|Geçirgen|`false`|`false`|`true`|  
  
 Bu özellikleri kullanarak bir derlemeyi ve türleri güvenlik açıklamalarını incelemek, geçerli güven düzeyine denetimi ve çalışma zamanının kuralları oluşturmaya çalışırken daha çok daha kolaydır. Örneğin, bir koruma alanlı uygulama etki alanında çalıştırıldığında aynı türü güvenlik açısından kritik komut satırından çalıştırdığınızda ya da güvenlik açısından saydam olabilir.  
  
 Benzer özellikleri vardır <xref:System.Reflection.MethodBase>, <xref:System.Reflection.FieldInfo>, <xref:System.Reflection.Emit.TypeBuilder>, <xref:System.Reflection.Emit.MethodBuilder>, ve <xref:System.Reflection.Emit.DynamicMethod> sınıfları. (Soyutlama diğer yansıma ve yansıma yayma, ilişkili yöntemler; Örneğin, özellikler için özellik erişimcileri uygulandıkları söz konusu olduğunda güvenlik öznitelikleri uygulanır.)  
  
<a name="accessingNormallyInaccessible"></a>   
## <a name="accessing-members-that-are-normally-inaccessible"></a>Normalde erişilemez üyelerine erişme  
 Ortak dil çalışma zamanı erişilebilirlik kurallara göre erişilemeyen üyeler çağırmak için yansıma kullanmak için kodunuzu bir veya iki verilmesi gerekir:  
  
-   Ortak olmayan herhangi bir üye çağırmak için kodu izin verecek şekilde: kodunuzu verilmelidir <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> bayrağı.  
  
    > [!NOTE]
    >  Varsayılan olarak, güvenlik ilkesi, Internet'ten kaynaklanan kod bu izni engeller. Bu izne hiçbir zaman Internet'ten kaynaklanan kod verilmelidir.  
  
-   Çağrılan üye içeren derleme izin kümesi ile aynı olduğu sürece, herhangi özel bir üye çağırmak için kodu veya bir alt kümesini, derleme izin kümesi izin vermek için çağıran kodu içerir: Kodunuzu verilmelidir <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrağı.  
  
 Örneğin, Internet izinleri artı bir uygulama etki alanı verin varsayalım <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> bayrak ve ardından bir Internet uygulaması iki derlemeleriyle A ve b çalıştırın  
  
-   Derleme B izin kümesi A verilmedi herhangi bir izni içermediğinden derlemesi, derleme B özel üyelerine erişmek için yansıma kullanabilirsiniz.  
  
-   Özel üyelerine erişmek için yansıma derlemesi kullanamaz [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] mscorlib.dll gibi derlemeleri mscorlib.dll tam olarak güvenilirdir ve bu nedenle A. derlemeye verilmemiş izinleri olduğundan A <xref:System.MemberAccessException> kod erişimi güvenliği, çalışma zamanında yığın gösterilmektedir oluşturulur.  
  
## <a name="serialization"></a>Serileştirme  
 Seri hale getirme, <xref:System.Security.Permissions.SecurityPermission> ile <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A?displayProperty=nameWithType> bayrağını alma ve erişilebilirlik bağımsız olarak seri hale getirilebilir türlerin üyelerini ayarlama olanağı sağlar. Bu izne bulmak ve bir örnek özel durumunu değiştirmek kod sağlar. (Uygun izinleri verilen ek olarak, türü olmalıdır [işaretlenmiş](../../../docs/standard/attributes/applying-attributes.md) meta verilerinde serileştirilebilir.)  
  
## <a name="parameters-of-type-methodinfo"></a>Tür MethodInfo parametreleri  
 Genel üyeler Süren yazılmasını önlemek <xref:System.Reflection.MethodInfo> özellikle Güvenilen kod için parametreleri. Bu tür üyeleri için kötü amaçlı bir kodun daha savunmasız olabilir. Örneğin, bir ortak üye alan yüksek derecede güvenilen kodda düşünün bir <xref:System.Reflection.MethodInfo> parametresi. Genel üye dolaylı çağrı yaptığını varsayalım <xref:System.Reflection.MethodBase.Invoke%2A> sağlanan parametre yöntemi. Genel üye çağrısı gerekli izni denetimleri yapmazsa <xref:System.Reflection.MethodBase.Invoke%2A> yöntemi her zaman başarılı olur, güvenlik sistemi çağıran yüksek oranda güvenilir olduğunu belirlediğinden. Kötü amaçlı kod doğrudan yöntem çağırma izni yok olsa bile, yine de dolaylı olarak bu nedenle ortak üye çağrısı yaparak bunu yapabilirsiniz.  
  
## <a name="version-information"></a>Sürüm Bilgileri  
  
-   İle başlayarak [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)], saydam kod güvenlik kritik üyelere erişim için yansıma kullanamazsınız.  
  
-   <xref:System.Security.Permissions.ReflectionPermissionFlag.RestrictedMemberAccess?displayProperty=nameWithType> Bayrağı sunulmuştur [!INCLUDE[net_v20SP1_long](../../../includes/net-v20sp1-long-md.md)]. Önceki sürümlerini [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] gerektiren <xref:System.Security.Permissions.ReflectionPermissionFlag.MemberAccess?displayProperty=nameWithType> ortak olmayan üyelere erişmek için yansımayı kullanan kod için bayrak. Kısmen güvenilen koda hiçbir zaman verilen bir izni budur.  
  
-   İle başlayarak [!INCLUDE[dnprdnlong](../../../includes/dnprdnlong-md.md)], ortak olmayan türler ve üyeler hakkında bilgi edinmek için yansıma kullanarak herhangi bir izni gerektirmez. Önceki sürümlerde <xref:System.Security.Permissions.ReflectionPermission> ile <xref:System.Security.Permissions.ReflectionPermissionFlag.TypeInformation?displayProperty=nameWithType> bayrağı gereklidir.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Security.Permissions.ReflectionPermissionFlag>
- <xref:System.Security.Permissions.ReflectionPermission>
- <xref:System.Security.Permissions.SecurityPermission>
- [Güvenlik Değişiklikleri](../../../docs/framework/security/security-changes.md)
- [Kod Erişimi Güvenliği](../../../docs/framework/misc/code-access-security.md)
- [Yansıma Yaymadaki Güvenlik Sorunları](../../../docs/framework/reflection-and-codedom/security-issues-in-reflection-emit.md)
- [Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Öznitelikleri Uygulama](../../../docs/standard/attributes/applying-attributes.md)
- [Özel Özniteliklere Erişim](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)
