---
title: .NET 'te yansıma
description: .NET ' te yansımayı inceleyin. Yüklü derlemeler ve bunlar içinde tanımlanan türler (sınıflar, arabirimler, yapılar ve numaralandırmalar gibi) hakkında bilgi alın.
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
ms.openlocfilehash: 46c67595126af2c62b28d29983775943586a0b90
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865287"
---
# <a name="reflection-in-net"></a>.NET 'te yansıma

<xref:System.Reflection>Ad alanındaki sınıflar ile birlikte, <xref:System.Type?displayProperty=nameWithType> yüklü [derlemeler](../../standard/assembly/index.md) ve bunlar içinde tanımlanan türler ve [sınıflar](../../standard/base-types/common-type-system.md#classes), [arabirimler](../../standard/base-types/common-type-system.md#interfaces)ve değer türleri (yani, [yapılar](../../standard/base-types/common-type-system.md#structures) ve [numaralandırmalar](../../standard/base-types/common-type-system.md#enumerations)) hakkında bilgi edinmenizi sağlar. Ayrıca, çalışma zamanında tür örnekleri oluşturmak ve bunları çağırmak ve bunlara erişmek için yansıma de kullanabilirsiniz. Yansımanın belirli yönleri hakkında konular için bu genel bakışı sonundaki [Ilgili konular](#related_topics) bölümüne bakın.
  
[Ortak dil çalışma zamanı](../../standard/clr.md) yükleyicisi, aynı uygulama kapsamına sahip nesneler etrafında tanımlanmış sınırları oluşturan [uygulama etki alanlarını](../app-domains/application-domains.md)yönetir. Bu yönetim, her derlemenin uygun uygulama etki alanına yüklenmesini ve her derleme içindeki tür hiyerarşisinin bellek yerleşimini denetlemeyi içerir.  
  
[Derlemeler](../app-domains/index.md) modüller içerir, modüller türler içerir ve türler üye içerir. Yansıma derlemeleri, modülleri ve türleri kapsülleyen nesneler sağlar. Bir türün örneğini dinamik olarak oluşturmak, türü varolan bir nesneye bağlamak veya var olan bir nesneden türü almak için yansıma kullanabilirsiniz. Daha sonra türün yöntemlerini çağırabilir veya alan ve özelliklerine erişim sağlayabilirsiniz. Yansımanın tipik kullanımları şunları içerir:  
  
- <xref:System.Reflection.Assembly>Derlemeleri tanımlamak ve yüklemek, derleme bildiriminde listelenen modülleri yüklemek ve bu derlemeden bir tür bulmak ve bir örneğini oluşturmak için kullanın.  
  
- <xref:System.Reflection.Module>Modülünü ve modüldeki sınıfları içeren derleme gibi bilgileri bulma için kullanın. Ayrıca, modülde tanımlı tüm genel yöntemleri veya diğer özel, genel olmayan yöntemleri de alabilirsiniz.  
  
- <xref:System.Reflection.ConstructorInfo>Ad, parametreler, erişim değiştiricileri ( `public` veya gibi `private` ) ve `abstract` bir oluşturucunun uygulama ayrıntıları (veya gibi `virtual` ) gibi bilgileri bulma için kullanın. <xref:System.Type.GetConstructors%2A> <xref:System.Type.GetConstructor%2A> <xref:System.Type> Belirli bir oluşturucuyu çağırmak için bir veya metodunu kullanın.  
  
- <xref:System.Reflection.MethodInfo>Ad, dönüş türü, parametreler, erişim değiştiricileri ( `public` veya gibi `private` ) ve `abstract` bir yöntemin uygulama ayrıntıları (veya gibi) gibi bilgileri bulma için kullanın `virtual` . <xref:System.Type.GetMethods%2A> <xref:System.Type.GetMethod%2A> <xref:System.Type> Belirli bir yöntemi çağırmak için veya metodunu kullanın.  
  
- <xref:System.Reflection.FieldInfo>Bir alanın adı, erişim değiştiricileri ( `public` veya gibi `private` ) ve uygulama ayrıntılarını (gibi `static` ) ve alan değerlerini almak veya ayarlamak için kullanın.  
  
- <xref:System.Reflection.EventInfo>Ad, olay işleyicisi veri türü, özel öznitelikler, tür bildirme ve bir olayın yansıtılan türü ve olay işleyicilerini ekleme veya kaldırma gibi bilgileri bulma için kullanın.  
  
- <xref:System.Reflection.PropertyInfo>Ad, veri türü, bildirim türü, yansıtılan tür ve bir özelliğin salt okunurdur veya yazılabilir durumu gibi bilgileri öğrenmek ve özellik değerlerini almak veya ayarlamak için kullanın.  
  
- Parametrenin <xref:System.Reflection.ParameterInfo> adı, veri türü, bir parametrenin bir giriş veya çıkış parametresi olup olmadığı ve parametrenin bir yöntem imzasında konumu gibi bilgileri bulma için kullanın.  
  
- <xref:System.Reflection.CustomAttributeData>Bir uygulama etki alanının yalnızca yansıma bağlamında çalışırken özel öznitelikler hakkında bilgi edinmek için kullanın. <xref:System.Reflection.CustomAttributeData>öznitelikleri, örnekleri oluşturmadan incelemenizi sağlar.  
  
Ad alanının sınıfları, <xref:System.Reflection.Emit> çalışma zamanında türleri oluşturmanıza olanak sağlayan özelleştirilmiş bir yansıma biçimi sağlar.  
  
Yansıma Ayrıca, kullanıcıların tür seçmesini ve ardından bu türlerle ilgili bilgileri görüntülemesini sağlayan tarayıcı türü olarak adlandırılan uygulamalar oluşturmak için de kullanılabilir.  
  
Yansıma için başka kullanımlar vardır. JScript gibi dillere yönelik derleyiciler sembol tabloları oluşturmak için yansıma kullanır. Ad alanındaki sınıflar, <xref:System.Runtime.Serialization> verilere erişmek ve hangi alanların kalıcı olduğunu anlamak için yansıma kullanır. Ad alanındaki sınıflar, <xref:System.Runtime.Remoting> serileştirme aracılığıyla yansımayı dolaylı olarak kullanır.  
  
## <a name="runtime-types-in-reflection"></a>Yansımadaki Çalışma Zamanı Türleri  
Yansıma, <xref:System.Type> <xref:System.Reflection.MethodInfo> türleri, üyeleri, parametreleri ve diğer kod varlıklarını göstermek için ve gibi sınıflar sağlar. Ancak, yansıma kullandığınızda, en fazla soyut olan (Visual Basic) bu sınıflarla doğrudan çalışmanız gerekmez `MustInherit` . Bunun yerine, ortak dil çalışma zamanı (CLR) tarafından sunulan türlerle çalışırsınız.  
  
Örneğin, `typeof` `GetType` nesne almak için C# işlecini (Visual Basic) kullandığınızda <xref:System.Type> , nesne gerçekten bir olur `RuntimeType` . `RuntimeType`' dan türetilir <xref:System.Type> ve tüm soyut yöntemlerin uygulamalarını sağlar.  
  
Bu çalışma zamanı sınıfları `internal` ( `Friend` Visual Basic). Davranışları temel sınıf belgeleri tarafından açıklandığından, bunlar temel sınıflarından ayrı olarak açıklanmazlar.  
  
<a name="related_topics"></a>

## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Tür Bilgilerini Görüntüleme](viewing-type-information.md)|Sınıfını açıklar <xref:System.Type> ve <xref:System.Type> oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar hakkında bilgi edinmek için çeşitli yansıma sınıflarıyla birlikte nasıl kullanılacağını gösteren kod örnekleri sağlar.|  
|[Yansıma ve Genel Türler](reflection-and-generic-types.md)|Yansımanın tür parametrelerini ve genel türlerin tür bağımsız değişkenlerini ve genel yöntemleri nasıl işlediğini açıklar.|  
|[Yansımayla İlgili Güvenlik Konuları](security-considerations-for-reflection.md)|Tür bilgilerini ve erişim türlerini saptamak için hangi derece yansıma 'nin kullanılabileceğini belirlemek için kuralları açıklar.|  
|[Dinamik Olarak Yükleme ve Türleri Kullanma](dynamically-loading-and-using-types.md)|Geç bağlamayı destekleyen yansıma özel bağlama arabirimini açıklar.|  
|[Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme](how-to-load-assemblies-into-the-reflection-only-context.md)|Yalnızca yansıma yük bağlamını açıklar. Bir derlemenin nasıl yükleneceğini, bağlamını nasıl test leneceğini ve yalnızca yansıma bağlamındaki bir derlemeye uygulanan özniteliklerin nasıl incelenuygulanacağını gösterir.|  
|[Özel Özniteliklere Erişim](accessing-custom-attributes.md)|Öznitelik varlığını ve değerlerini sorgulamak için yansıma kullanımını gösterir.|  
|[Tam Olarak Nitelenmiş Tür Adlarını Belirtme](specifying-fully-qualified-type-names.md)|Backus-Naur form (BNF) ve özel karakterler, derleme adları, işaretçiler, başvurular ve diziler için gereken söz dizimi açısından tam nitelikli tür adlarının biçimini açıklar.|  
|[Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama](how-to-hook-up-a-delegate-using-reflection.md)|Bir yöntem için nasıl temsilci oluşturacağınızı ve temsilciyi bir olaya nasıl bağlanacağını açıklar. Kullanarak çalışma zamanında bir olay işleme yönteminin nasıl oluşturulacağını açıklar <xref:System.Reflection.Emit.DynamicMethod> .|  
|[Dinamik Yöntemleri ve Derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)|Dinamik derlemeler ve dinamik yöntemler oluşturmayı açıklar.|  
  
## <a name="reference"></a>Başvuru  

<xref:System.Type?displayProperty=nameWithType>  
  
<xref:System.Reflection>  
  
<xref:System.Reflection.Emit>  
