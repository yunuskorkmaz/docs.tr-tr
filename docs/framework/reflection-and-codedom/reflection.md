---
title: .NET 'te yansıma
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57f0a13a5e57898add667082d670de39431f940f
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/17/2019
ms.locfileid: "71045874"
---
# <a name="reflection-in-net"></a>.NET 'te yansıma

<xref:System.Reflection> Ad <xref:System.Type?displayProperty=nameWithType>alanındaki sınıflar ile birlikte, yüklü [derlemeler](../../standard/assembly/index.md) ve bunlar içinde tanımlanan türler ( [sınıflar](../../standard/base-types/common-type-system.md#classes), [arabirimler](../../standard/base-types/common-type-system.md#interfaces)ve [değer türleri](../../csharp/language-reference/keywords/value-types.md)gibi) hakkında bilgi edinmenizi sağlar. Ayrıca, çalışma zamanında tür örnekleri oluşturmak ve bunları çağırmak ve bunlara erişmek için yansıma de kullanabilirsiniz. Yansımanın belirli yönleri hakkında konular için bu genel bakışı sonundaki [Ilgili konular](#related_topics) bölümüne bakın.
  
[Ortak dil çalışma zamanı](../../standard/clr.md) yükleyicisi, aynı uygulama kapsamına sahip nesneler etrafında tanımlanmış sınırları oluşturan [uygulama etki alanlarını](../app-domains/application-domains.md)yönetir. Bu yönetim, her derlemenin uygun uygulama etki alanına yüklenmesini ve her derleme içindeki tür hiyerarşisinin bellek yerleşimini denetlemeyi içerir.  
  
[Derlemeler](../app-domains/index.md) modüller içerir, modüller türler içerir ve türler üye içerir. Yansıma derlemeleri, modülleri ve türleri kapsülleyen nesneler sağlar. Bir türün örneğini dinamik olarak oluşturmak, türü varolan bir nesneye bağlamak veya var olan bir nesneden türü almak için yansıma kullanabilirsiniz. Daha sonra türün yöntemlerini çağırabilir veya alan ve özelliklerine erişim sağlayabilirsiniz. Yansımanın tipik kullanımları şunları içerir:  
  
- Derlemeleri <xref:System.Reflection.Assembly> tanımlamak ve yüklemek, derleme bildiriminde listelenen modülleri yüklemek ve bu derlemeden bir tür bulmak ve bir örneğini oluşturmak için kullanın.  
  
- Modülünü <xref:System.Reflection.Module> ve modüldeki sınıfları içeren derleme gibi bilgileri bulma için kullanın. Ayrıca, modülde tanımlı tüm genel yöntemleri veya diğer özel, genel olmayan yöntemleri de alabilirsiniz.  
  
- Ad <xref:System.Reflection.ConstructorInfo> , parametreler, erişim değiştiricileri ( `public` veya `private`gibi `abstract` ) ve bir oluşturucunun uygulama ayrıntıları (veya `virtual`gibi) gibi bilgileri bulma için kullanın. Belirli bir oluşturucuyu <xref:System.Type.GetConstructor%2A> çağırmak için bir <xref:System.Type>veyametodunukullanın <xref:System.Type.GetConstructors%2A> .  
  
- Ad <xref:System.Reflection.MethodInfo> , dönüş türü, parametreler, erişim değiştiricileri ( `public` veya `private`gibi `abstract` ) ve bir yöntemin uygulama ayrıntıları (veya `virtual`gibi) gibi bilgileri bulma için kullanın. Belirli bir <xref:System.Type.GetMethod%2A> <xref:System.Type.GetMethods%2A> yöntemiçağırmakiçin<xref:System.Type> veya metodunu kullanın.  
  
- Bir <xref:System.Reflection.FieldInfo> alanın adı, erişim değiştiricileri ( `public` veya `private`gibi) ve uygulama ayrıntılarını ( `static`gibi) ve alan değerlerini almak veya ayarlamak için kullanın.  
  
- Ad <xref:System.Reflection.EventInfo> , olay işleyicisi veri türü, özel öznitelikler, tür bildirme ve bir olayın yansıtılan türü ve olay işleyicilerini ekleme veya kaldırma gibi bilgileri bulma için kullanın.  
  
- Ad <xref:System.Reflection.PropertyInfo> , veri türü, bildirim türü, yansıtılan tür ve bir özelliğin salt okunurdur veya yazılabilir durumu gibi bilgileri öğrenmek ve özellik değerlerini almak veya ayarlamak için kullanın.  
  
- Parametrenin <xref:System.Reflection.ParameterInfo> adı, veri türü, bir parametrenin bir giriş veya çıkış parametresi olup olmadığı ve parametrenin bir yöntem imzasında konumu gibi bilgileri bulma için kullanın.  
  
- Bir <xref:System.Reflection.CustomAttributeData> uygulama etki alanının yalnızca yansıma bağlamında çalışırken özel öznitelikler hakkında bilgi edinmek için kullanın. <xref:System.Reflection.CustomAttributeData>öznitelikleri, örnekleri oluşturmadan incelemenizi sağlar.  
  
<xref:System.Reflection.Emit> Ad alanının sınıfları, çalışma zamanında türleri oluşturmanıza olanak sağlayan özelleştirilmiş bir yansıma biçimi sağlar.  
  
Yansıma Ayrıca, kullanıcıların tür seçmesini ve ardından bu türlerle ilgili bilgileri görüntülemesini sağlayan tarayıcı türü olarak adlandırılan uygulamalar oluşturmak için de kullanılabilir.  
  
Yansıma için başka kullanımlar vardır. JScript gibi dillere yönelik derleyiciler sembol tabloları oluşturmak için yansıma kullanır. <xref:System.Runtime.Serialization> Ad alanındaki sınıflar, verilere erişmek ve hangi alanların kalıcı olduğunu anlamak için yansıma kullanır. <xref:System.Runtime.Remoting> Ad alanındaki sınıflar, serileştirme aracılığıyla yansımayı dolaylı olarak kullanır.  
  
## <a name="runtime-types-in-reflection"></a>Yansımadaki Çalışma Zamanı Türleri  
Yansıma, türleri, üyeleri, <xref:System.Type> parametreleri <xref:System.Reflection.MethodInfo>ve diğer kod varlıklarını göstermek için ve gibi sınıflar sağlar. Ancak, yansıma kullandığınızda, en fazla soyut olan (`MustInherit` Visual Basic) bu sınıflarla doğrudan çalışmanız gerekmez. Bunun yerine, ortak dil çalışma zamanı (CLR) tarafından sunulan türlerle çalışırsınız.  
  
Örneğin C# `typeof` , bir`GetType` `RuntimeType`nesneyialmakiçin işlecini (Visual Basic) kullandığınızda, nesne gerçekten bir olur. <xref:System.Type> `RuntimeType`' dan <xref:System.Type> türetilir ve tüm soyut yöntemlerin uygulamalarını sağlar.  
  
Bu çalışma zamanı sınıfları `internal` (`Friend` Visual Basic). Davranışları temel sınıf belgeleri tarafından açıklandığından, bunlar temel sınıflarından ayrı olarak açıklanmazlar.  
  
<a name="related_topics"></a>   

## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Tür Bilgilerini Görüntüleme](viewing-type-information.md)|Sınıfını açıklar ve oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar <xref:System.Type> hakkında bilgi edinmek için çeşitli yansıma sınıflarıyla birlikte nasıl kullanılacağını gösteren kod örnekleri sağlar. <xref:System.Type>|  
|[Yansıma ve Genel Türler](reflection-and-generic-types.md)|Yansımanın tür parametrelerini ve genel türlerin tür bağımsız değişkenlerini ve genel yöntemleri nasıl işlediğini açıklar.|  
|[Yansımayla İlgili Güvenlik Konuları](security-considerations-for-reflection.md)|Tür bilgilerini ve erişim türlerini saptamak için hangi derece yansıma 'nin kullanılabileceğini belirlemek için kuralları açıklar.|  
|[Türleri Dinamik Olarak Yükleme ve Kullanma](dynamically-loading-and-using-types.md)|Geç bağlamayı destekleyen yansıma özel bağlama arabirimini açıklar.|  
|[Nasıl yapılır: Derlemeleri yalnızca yansıma Içeriğine yükle](how-to-load-assemblies-into-the-reflection-only-context.md)|Yalnızca yansıma yük bağlamını açıklar. Bir derlemenin nasıl yükleneceğini, bağlamını nasıl test leneceğini ve yalnızca yansıma bağlamındaki bir derlemeye uygulanan özniteliklerin nasıl incelenuygulanacağını gösterir.|  
|[Özel Özniteliklere Erişim](accessing-custom-attributes.md)|Öznitelik varlığını ve değerlerini sorgulamak için yansıma kullanımını gösterir.|  
|[Tam Olarak Nitelenmiş Tür Adlarını Belirtme](specifying-fully-qualified-type-names.md)|Backus-Naur form (BNF) ve özel karakterler, derleme adları, işaretçiler, başvurular ve diziler için gereken söz dizimi açısından tam nitelikli tür adlarının biçimini açıklar.|  
|[Nasıl yapılır: Yansıma kullanarak temsilci bağlama](how-to-hook-up-a-delegate-using-reflection.md)|Bir yöntem için nasıl temsilci oluşturacağınızı ve temsilciyi bir olaya nasıl bağlanacağını açıklar. Kullanarak <xref:System.Reflection.Emit.DynamicMethod>çalışma zamanında bir olay işleme yönteminin nasıl oluşturulacağını açıklar.|  
|[Dinamik Yöntemleri ve Derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)|Dinamik derlemeler ve dinamik yöntemler oluşturmayı açıklar.|  
  
## <a name="reference"></a>Başvuru  

<xref:System.Type?displayProperty=nameWithType>  
  
<xref:System.Reflection>  
  
<xref:System.Reflection.Emit>  
