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
ms.openlocfilehash: 42944d8267d2e99fd9eb1a2cb28c0c81d3e9af75
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744575"
---
# <a name="reflection-in-net"></a>.NET 'te yansıma

<xref:System.Reflection> ad alanındaki [sınıflar, <xref:System.Type?displayProperty=nameWithType>](../../standard/base-types/common-type-system.md#interfaces)ile birlikte, yüklü [derlemeler](../../standard/assembly/index.md) ve bunlar içinde tanımlanan türler [(örneğin,](../../standard/base-types/common-type-system.md#classes) [yapılar](../../standard/base-types/common-type-system.md#structures) ve [numaralandırmalar](../../standard/base-types/common-type-system.md#enumerations)) hakkında bilgi edinmenizi sağlar. Ayrıca, çalışma zamanında tür örnekleri oluşturmak ve bunları çağırmak ve bunlara erişmek için yansıma de kullanabilirsiniz. Yansımanın belirli yönleri hakkında konular için bu genel bakışı sonundaki [Ilgili konular](#related_topics) bölümüne bakın.
  
[Ortak dil çalışma zamanı](../../standard/clr.md) yükleyicisi, aynı uygulama kapsamına sahip nesneler etrafında tanımlanmış sınırları oluşturan [uygulama etki alanlarını](../app-domains/application-domains.md)yönetir. Bu yönetim, her derlemenin uygun uygulama etki alanına yüklenmesini ve her derleme içindeki tür hiyerarşisinin bellek yerleşimini denetlemeyi içerir.  
  
[Derlemeler](../app-domains/index.md) modüller içerir, modüller türler içerir ve türler üye içerir. Yansıma derlemeleri, modülleri ve türleri kapsülleyen nesneler sağlar. Bir türün örneğini dinamik olarak oluşturmak, türü varolan bir nesneye bağlamak veya var olan bir nesneden türü almak için yansıma kullanabilirsiniz. Daha sonra türün yöntemlerini çağırabilir veya alan ve özelliklerine erişim sağlayabilirsiniz. Yansımanın tipik kullanımları şunları içerir:  
  
- Derlemeleri tanımlamak ve yüklemek, derleme bildiriminde listelenen modülleri yüklemek ve bu derlemeden bir tür bulmak ve bir örneğini oluşturmak için <xref:System.Reflection.Assembly> kullanın.  
  
- Modülünü ve modüldeki sınıfları içeren derleme gibi bilgileri öğrenmek için <xref:System.Reflection.Module> kullanın. Ayrıca, modülde tanımlı tüm genel yöntemleri veya diğer özel, genel olmayan yöntemleri de alabilirsiniz.  
  
- Ad, parametreler, erişim değiştiriciler (`public` veya `private`gibi) ve bir oluşturucunun uygulama ayrıntıları (örneğin `abstract` veya `virtual`) gibi bilgileri öğrenmek için <xref:System.Reflection.ConstructorInfo> kullanın. Belirli bir oluşturucuyu çağırmak için bir <xref:System.Type> <xref:System.Type.GetConstructors%2A> veya <xref:System.Type.GetConstructor%2A> metodunu kullanın.  
  
- Ad, dönüş türü, parametreler, erişim değiştiricileri (`public` veya `private`gibi) ve bir yöntemin uygulama ayrıntıları (örneğin `abstract` veya `virtual`) gibi bilgileri öğrenmek için <xref:System.Reflection.MethodInfo> kullanın. Belirli bir yöntemi çağırmak için bir <xref:System.Type> <xref:System.Type.GetMethods%2A> veya <xref:System.Type.GetMethod%2A> metodunu kullanın.  
  
- Bir alanın adı, erişim değiştiricileri (`public` veya `private`) ve uygulama ayrıntılarını (örneğin `static`) ve alan değerlerini almak veya ayarlamak gibi bilgileri öğrenmek için <xref:System.Reflection.FieldInfo> kullanın.  
  
- Ad, olay işleyicisi veri türü, özel öznitelikler, tür bildirme ve bir olayın yansıtılan türü ve olay işleyicilerini ekleme veya kaldırma gibi bilgileri öğrenmek için <xref:System.Reflection.EventInfo> kullanın.  
  
- Ad, veri türü, bildirim türü, yansıtılan tür ve bir özelliğin salt okunurdur veya yazılabilir durumu gibi bilgileri öğrenmek ve özellik değerlerini almak veya ayarlamak için <xref:System.Reflection.PropertyInfo> kullanın.  
  
- Bir parametrenin adı, veri türü, bir parametrenin bir giriş veya çıkış parametresi olup olmadığı ve parametrenin bir yöntem imzasında konumunun konumunu öğrenmek için <xref:System.Reflection.ParameterInfo> kullanın.  
  
- Bir uygulama etki alanının yalnızca yansıma bağlamında çalışırken özel öznitelikler hakkında bilgi edinmek için <xref:System.Reflection.CustomAttributeData> kullanın. <xref:System.Reflection.CustomAttributeData>, özniteliklerini oluşturmaksızın öznitelikleri incelemenizi sağlar.  
  
<xref:System.Reflection.Emit> ad alanının sınıfları, çalışma zamanında türleri derlemenize olanak sağlayan özelleştirilmiş bir yansıma biçimi sağlar.  
  
Yansıma Ayrıca, kullanıcıların tür seçmesini ve ardından bu türlerle ilgili bilgileri görüntülemesini sağlayan tarayıcı türü olarak adlandırılan uygulamalar oluşturmak için de kullanılabilir.  
  
Yansıma için başka kullanımlar vardır. JScript gibi dillere yönelik derleyiciler sembol tabloları oluşturmak için yansıma kullanır. <xref:System.Runtime.Serialization> ad alanındaki sınıflar, verilere erişmek ve hangi alanların kalıcı hale getirileyeceğini anlamak için yansıma kullanır. <xref:System.Runtime.Remoting> ad alanındaki sınıflar, serileştirme aracılığıyla yansımayı dolaylı olarak kullanır.  
  
## <a name="runtime-types-in-reflection"></a>Yansımadaki Çalışma Zamanı Türleri  
Yansıma, türleri, üyeleri, parametreleri ve diğer kod varlıklarını göstermek için <xref:System.Type> ve <xref:System.Reflection.MethodInfo>gibi sınıflar sağlar. Ancak, yansıma kullandığınızda, çoğu soyut olan (Visual Basic`MustInherit`) bu sınıflarla doğrudan çalışmanız gerekmez. Bunun yerine, ortak dil çalışma zamanı (CLR) tarafından sunulan türlerle çalışırsınız.  
  
Örneğin, bir <xref:System.Type> nesnesi elde etmek C# için `typeof` işlecini (Visual Basic`GetType`) kullandığınızda, nesne gerçekten bir `RuntimeType`. `RuntimeType` <xref:System.Type> türetilir ve tüm soyut yöntemlerin uygulamalarını sağlar.  
  
Bu çalışma zamanı sınıfları `internal` (Visual Basic`Friend`). Davranışları temel sınıf belgeleri tarafından açıklandığından, bunlar temel sınıflarından ayrı olarak açıklanmazlar.  
  
<a name="related_topics"></a>   

## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Tür Bilgilerini Görüntüleme](viewing-type-information.md)|<xref:System.Type> sınıfını açıklar ve oluşturucular, Yöntemler, alanlar, Özellikler ve olaylar hakkında bilgi edinmek için <xref:System.Type> çeşitli yansıma sınıflarıyla nasıl kullanacağınızı gösteren kod örnekleri sağlar.|  
|[Yansıma ve Genel Türler](reflection-and-generic-types.md)|Yansımanın tür parametrelerini ve genel türlerin tür bağımsız değişkenlerini ve genel yöntemleri nasıl işlediğini açıklar.|  
|[Yansımayla İlgili Güvenlik Konuları](security-considerations-for-reflection.md)|Tür bilgilerini ve erişim türlerini saptamak için hangi derece yansıma 'nin kullanılabileceğini belirlemek için kuralları açıklar.|  
|[Türleri Dinamik Olarak Yükleme ve Kullanma](dynamically-loading-and-using-types.md)|Geç bağlamayı destekleyen yansıma özel bağlama arabirimini açıklar.|  
|[Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme](how-to-load-assemblies-into-the-reflection-only-context.md)|Yalnızca yansıma yük bağlamını açıklar. Bir derlemenin nasıl yükleneceğini, bağlamını nasıl test leneceğini ve yalnızca yansıma bağlamındaki bir derlemeye uygulanan özniteliklerin nasıl incelenuygulanacağını gösterir.|  
|[Özel Özniteliklere Erişim](accessing-custom-attributes.md)|Öznitelik varlığını ve değerlerini sorgulamak için yansıma kullanımını gösterir.|  
|[Tam Olarak Nitelenmiş Tür Adlarını Belirtme](specifying-fully-qualified-type-names.md)|Backus-Naur form (BNF) ve özel karakterler, derleme adları, işaretçiler, başvurular ve diziler için gereken söz dizimi açısından tam nitelikli tür adlarının biçimini açıklar.|  
|[Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama](how-to-hook-up-a-delegate-using-reflection.md)|Bir yöntem için nasıl temsilci oluşturacağınızı ve temsilciyi bir olaya nasıl bağlanacağını açıklar. <xref:System.Reflection.Emit.DynamicMethod>kullanarak çalışma zamanında olay işleme yönteminin nasıl oluşturulacağını açıklar.|  
|[Dinamik Yöntemleri ve Derlemeleri Yayma](emitting-dynamic-methods-and-assemblies.md)|Dinamik derlemeler ve dinamik yöntemler oluşturmayı açıklar.|  
  
## <a name="reference"></a>Başvuru  

<xref:System.Type?displayProperty=nameWithType>  
  
<xref:System.Reflection>  
  
<xref:System.Reflection.Emit>  
