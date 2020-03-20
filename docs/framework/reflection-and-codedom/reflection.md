---
title: .NET'te Yansıma
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET], reflection
- EventInfo class, reflection
- common language runtime, reflection
- FieldInfo class, reflection
- ParameterInfo class, reflection
- ConstructorInfo class, reflection
- Assembly class, reflection
- value types, reflection
- reflection, about reflection
- modules, reflection
- runtime, reflection
- Module class, reflection
- MethodInfo class, reflection
- PropertyInfo class, reflection
- type browsers
- reflection
- discovering type information at run time
- type system, reflection
ms.assetid: d1a58e7f-fb39-4d50-bf84-e3b8f9bf9775
ms.openlocfilehash: 90d9cf4c473d73d1eeeb5f2a1098f8626c20359f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79180483"
---
# <a name="reflection-in-net"></a>.NET'te Yansıma

<xref:System.Reflection> Ad alanındaki <xref:System.Type?displayProperty=nameWithType>sınıflar, yüklenen [derlemeler](../../standard/assembly/index.md) ve [sınıflar,](../../standard/base-types/common-type-system.md#classes) [arabirimler](../../standard/base-types/common-type-system.md#interfaces)ve değer türleri (yani [yapılar](../../standard/base-types/common-type-system.md#structures) ve [sayısallaştırmalar)](../../standard/base-types/common-type-system.md#enumerations)gibi bunlar içinde tanımlanan türler hakkında bilgi edinmenizi sağlar. Yansıtmayı, çalışma zamanında tür örnekleri oluşturmak ve bunları çağırmak ve bunlara erişmek için de kullanabilirsiniz. Yansımanın belirli yönleri yle ilgili konular için, bu genel bakışın sonunda [İlgili konulara](#related_topics) bakın.
  
[Ortak dil runtime](../../standard/clr.md) yükleyici, aynı uygulama kapsamına sahip nesnelerin etrafında tanımlı sınırları oluşturan [uygulama etki alanlarını](../app-domains/application-domains.md)yönetir. Bu yönetim, her derlemeyi uygun uygulama etki alanına yüklemeyi ve her derlemeiçindeki tür hiyerarşisinin bellek düzenini denetlemeyi içerir.  
  
[Derlemeler](../app-domains/index.md) modüller içerir, modüller türleri içerir ve türleri üye içerir. Yansıma, derlemeleri, modülleri ve türleri kapsülleyen nesneler sağlar. Yansımayı dinamik olarak bir tür örneği oluşturmak, türü varolan bir nesneye bağlamak veya türü varolan bir nesneden almak için kullanabilirsiniz. Daha sonra türün yöntemlerini çağırabilir veya alanlarına ve özelliklerine erişebilirsiniz. Yansımanın tipik kullanımları şunlardır:  
  
- Derlemeleri tanımlamak ve yüklemek, montaj bildiriminde listelenen modülleri yüklemek ve bu derlemeden bir tür bulmak ve bunun bir örneğini oluşturmak için kullanın. <xref:System.Reflection.Assembly>  
  
- Modülü <xref:System.Reflection.Module> ve modüldeki sınıfları içeren derleme gibi bilgileri keşfetmek için kullanın. Ayrıca, modülde tanımlanan tüm genel yöntemleri veya diğer spesifik, küresel olmayan yöntemleri de alabilirsiniz.  
  
- Bir <xref:System.Reflection.ConstructorInfo> oluşturucunun adı, parametreleri, erişim değiştiriciler `public` `private`(örneğin veya), ve `abstract` `virtual`uygulama ayrıntıları (gibi) gibi bilgileri keşfetmek için kullanın. Belirli <xref:System.Type.GetConstructors%2A> bir <xref:System.Type.GetConstructor%2A> oluşturucuyu çağırmak için a'nın <xref:System.Type> yöntemini kullanın.  
  
- Bir <xref:System.Reflection.MethodInfo> yöntemin adı, iade türü, parametreler, erişim değiştiriciler `public` `private`(örneğin veya), ve `abstract` `virtual`uygulama ayrıntıları (gibi veya) gibi bilgileri keşfetmek için kullanın. Belirli <xref:System.Type.GetMethods%2A> bir <xref:System.Type.GetMethod%2A> yöntemi <xref:System.Type> çağırmak için a'nın yöntemini kullanın.  
  
- Bir <xref:System.Reflection.FieldInfo> alanın adı, erişim değiştiriciler `public` (örneğin veya) `private`ve uygulama ayrıntıları `static`(örneğin) gibi bilgileri keşfetmek ve alan değerlerini almak veya ayarlamak için kullanın.  
  
- Ad, olay işleyicisi veri türü, özel öznitelikler, bildirim türü ve yansıtılan olay türü gibi bilgileri bulmak ve olay işleyicileri eklemek veya kaldırmak için kullanın. <xref:System.Reflection.EventInfo>  
  
- Ad, veri türü, beyan türü, yansıyan tür ve bir özelliğin salt okunur veya yazılabilir durumu gibi bilgileri bulmak ve özellik değerlerini almak veya ayarlamak için kullanın. <xref:System.Reflection.PropertyInfo>  
  
- Parametrenin adı, veri türü, parametrenin giriş veya çıktı parametresi olup olmadığı ve parametrenin yöntem imzasındaki konumu gibi bilgileri keşfetmek için kullanın. <xref:System.Reflection.ParameterInfo>  
  
- Bir <xref:System.Reflection.CustomAttributeData> uygulama etki alanının yalnızca yansıma bağlamında çalışırken özel öznitelikler hakkındaki bilgileri keşfetmek için kullanın. <xref:System.Reflection.CustomAttributeData>örneklerini oluşturmadan öznitelikleri incelemenizi sağlar.  
  
<xref:System.Reflection.Emit> Ad alanının sınıfları, çalışma zamanında türler oluşturmanıza olanak tanıyan özel bir yansıma biçimi sağlar.  
  
Yansıma, kullanıcıların türleri seçmesini ve daha sonra bu türlerle ilgili bilgileri görüntülemesini sağlayan tür tarayıcılar adı verilen uygulamalar oluşturmak için de kullanılabilir.  
  
Yansıma için başka kullanımalanları da vardır. JScript gibi dillerin derleyicileri, sembol tabloları oluşturmak için yansımayı kullanır. <xref:System.Runtime.Serialization> Ad alanındaki sınıflar, verilere erişmek ve hangi alanların devam edinceye kadar süreceğini belirlemek için yansımayı kullanır. <xref:System.Runtime.Remoting> Ad alanındaki sınıflar, serileştirme yoluyla dolaylı olarak yansıma kullanır.  
  
## <a name="runtime-types-in-reflection"></a>Yansımadaki Çalışma Zamanı Türleri  
Yansıma, türleri, <xref:System.Type> üyeleri, parametreleri ve <xref:System.Reflection.MethodInfo>diğer kod varlıklarını temsil etmek için sınıflar sağlar. Ancak, yansıma kullandığınızda, doğrudan bu sınıflar ile çalışmaz, bunların`MustInherit` çoğu soyut (Visual Basic). Bunun yerine, ortak dil çalışma zamanı (CLR) tarafından sağlanan türleri ile çalışırsınız.  
  
Örneğin, `typeof` bir`GetType` <xref:System.Type> nesne elde etmek için C# işleci (Visual Basic'te) kullandığınızda, nesne gerçekten bir `RuntimeType`. `RuntimeType`tüm soyut <xref:System.Type> yöntemlerden türetilmiştir ve uygulanmasını sağlar.  
  
Bu çalışma zamanı `internal` `Friend` sınıfları (Visual Basic'te) vardır. Davranışları taban sınıf belgeleri tarafından açıklandığıiçin, temel sınıflarından ayrı olarak belgelenmezler.  
  
<a name="related_topics"></a>

## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Tür Bilgilerini Görüntüleme](viewing-type-information.md)|<xref:System.Type> Sınıfı açıklar ve oluşturucular, yöntemler, alanlar, özellikler ve olaylar hakkında bilgi edinmek için çeşitli yansıma sınıflarıyla nasıl kullanılacağını <xref:System.Type> gösteren kod örnekleri sağlar.|  
|[Yansıma ve Genel Türler](reflection-and-generic-types.md)|Yansımanın genel türlerin ve genel yöntemlerin tür parametrelerini ve tür bağımsız değişkenlerini nasıl işleyeceğini açıklar.|  
|[Yansımayla İlgili Güvenlik Konuları](security-considerations-for-reflection.md)|Tür bilgilerini ve erişim türlerini keşfetmek için hangi derece yansımanın kullanılabileceğini belirleyen kuralları açıklar.|  
|[Türleri Dinamik Olarak Yükleme ve Kullanma](dynamically-loading-and-using-types.md)|Geç bağlamayı destekleyen yansıma özel bağlama arabirimini açıklar.|  
|[Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme](how-to-load-assemblies-into-the-reflection-only-context.md)|Yalnızca yansıma yük bağlamını açıklar. Bir derlemenin nasıl yüklenir, bağlamın nasıl sınanacağı ve yalnızca yansıma bağlamında bir derlemeye uygulanan özniteliklerin nasıl incelenir olduğunu gösterir.|  
|[Özel Özniteliklere Erişim](accessing-custom-attributes.md)|Sorgu öznitelik varlığı ve değerleri yansıtma kullanarak gösterir.|  
|[Tam Olarak Nitelenmiş Tür Adlarını Belirtme](specifying-fully-qualified-type-names.md)|Backus-Naur formu (BNF) açısından tam nitelikli tür adlarının biçimini ve özel karakterler, derleme adları, işaretçiler, başvurular ve diziler belirtmek için gereken sözdizimini açıklar.|  
|[Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama](how-to-hook-up-a-delegate-using-reflection.md)|Bir yöntem için temsilci oluşturmanın ve temsilcinin bir olaya nasıl bağlanın. Çalıştırılaç zamanında olay işleme yönteminin <xref:System.Reflection.Emit.DynamicMethod>nasıl oluşturulturun.|  
|[Dinamik Yöntemleri ve Derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)|Dinamik derlemelerin ve dinamik yöntemlerin nasıl üretilebildiğini açıklar.|  
  
## <a name="reference"></a>Başvuru  

<xref:System.Type?displayProperty=nameWithType>  
  
<xref:System.Reflection>  
  
<xref:System.Reflection.Emit>  
