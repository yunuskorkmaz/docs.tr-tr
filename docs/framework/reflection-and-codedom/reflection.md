---
title: ".NET Framework'te Yansıma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- assemblies [.NET Framework], reflection
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
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9b131b8b66315ffbb769eab059142f729cfaf2a2
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="reflection-in-the-net-framework"></a>.NET Framework'te Yansıma
Sınıflarda <xref:System.Reflection> ad alanı, birlikte <xref:System.Type?displayProperty=nameWithType>, yüklenen hakkında bilgi edinmek etkinleştirmeniz [derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) ve bunların içinde gibi tanımlanan türleri [sınıfları](http://msdn.microsoft.com/library/ad7d3561-271e-4546-82fc-e00b059f27a9), [arabirimleri](http://msdn.microsoft.com/library/fd9d5975-5363-4bc9-b883-609f887895e5), ve [değer türleri](http://msdn.microsoft.com/library/c9c567f8-8ab1-4d88-834d-00f7d92418de). Yansıma, çalışma zamanında tür örnekleri oluşturmak ve çağırma ve bunlara erişmek için de kullanabilirsiniz. Yansıma belirli yönlerini ilgili konular için bkz: [ilgili konular](#related_topics) bu genel bakışta, sonunda.  
  
 [Ortak dil çalışma zamanı](../../../docs/standard/clr.md) yükleyicisi yönetir [uygulama etki alanları](../../../docs/framework/app-domains/application-domains.md), aynı uygulama kapsama sahip nesneleri etrafında sınırlar tanımlanan hangi oluşturur. Bu yönetim uygun uygulama etki alanına her derlemesi yüklenirken ve her derleme içinde tür hiyerarşisini bellek düzenini denetleme içerir.  
  
 [Derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) türlerini içeren üyeleri modülleri içerir ve modülleri türleri içerir. Yansıma derlemeler, modüller ve türleri kapsülleyen nesneleri sağlar. Yansıma dinamik olarak bir türünün bir örneği oluşturmak, varolan bir nesneye Bağ türü veya varolan bir nesneden türünü almak için kullanabilirsiniz. Tür yöntemlerini çağıran veya özellikleri ve alanları erişim. Yansıma tipik kullanımları şunları içerir:  
  
-   Kullanım <xref:System.Reflection.Assembly> tanımlamak ve derlemelerini yüklemek için derleme bildiriminde listelenen ve bu derleme türünden bulup bir örneğini oluşturmak modülleri yükleme.  
  
-   Kullanım <xref:System.Reflection.Module> modülü ve modülde sınıfları içeren derlemenin gibi bilgileri bulmak için. Tüm genel yöntemler veya modülde tanımlanan diğer belirli, Global olmayan yöntemler de alabilirsiniz.  
  
-   Kullanım <xref:System.Reflection.ConstructorInfo> parametre adı gibi bilgileri bulmak için erişim değiştiricileri (gibi `public` veya `private`) ve uygulama ayrıntıları (gibi `abstract` veya `virtual`) bir oluşturucunun. Kullanım <xref:System.Type.GetConstructors%2A> veya <xref:System.Type.GetConstructor%2A> yöntemi bir <xref:System.Type> belirli bir oluşturucu çağrılamıyor.  
  
-   Kullanım <xref:System.Reflection.MethodInfo> adı gibi bilgileri bulmak için dönüş türü, parametreleri, erişim değiştiricileri (gibi `public` veya `private`) ve uygulama ayrıntıları (gibi `abstract` veya `virtual`) bir yöntem. Kullanım <xref:System.Type.GetMethods%2A> veya <xref:System.Type.GetMethod%2A> yöntemi bir <xref:System.Type> belirli bir yöntemi çağırmak için.  
  
-   Kullanım <xref:System.Reflection.FieldInfo> adı gibi bilgileri bulmak için erişim değiştiricileri (gibi `public` veya `private`) ve uygulama ayrıntıları (gibi `static`), bir alanın ve almak veya alan değerlerini ayarlamak için.  
  
-   Kullanım <xref:System.Reflection.EventInfo> ad, olay işleyici veri türü, türü ve bir olay yansıtılan türünü bildirme özel öznitelikleri gibi bilgileri bulmak ve eklemek veya olay işleyicileri kaldırmak için.  
  
-   Kullanım <xref:System.Reflection.PropertyInfo> adı gibi bilgileri bulmak için türü, veri türü, türü, bildirme yansıtılır ve bir özelliğin ve almak veya özellik değerlerini ayarlamak için salt okunur veya yazılabilir durumu.  
  
-   Kullanım <xref:System.Reflection.ParameterInfo> bir parametrenin adı gibi bilgileri bulmak için veri türü, bir parametre bir giriş veya çıkış parametresi ve yöntem imzası parametresi konumda olup olmadığını.  
  
-   Kullanım <xref:System.Reflection.CustomAttributeData> uygulama etki alanı salt yansıma bağlamında çalışırken özel öznitelikler hakkında bilgi bulmak için. <xref:System.Reflection.CustomAttributeData>bunların örneklerini oluşturmak zorunda kalmadan öznitelikleri incelemenize olanak tanır.  
  
 Sınıflarını <xref:System.Reflection.Emit> ad alanı türleri çalışma zamanında oluşturmanıza olanak sağlayan yansıma özel biçimi sağlayın.  
  
 Yansıma türlerini seçin ve ardından bu türleri hakkındaki bilgileri görüntülemek kullanıcıların tür tarayıcıları olarak adlandırılan uygulamaları oluşturmak için de kullanılabilir.  
  
 Diğer kullanımlar için yansıma vardır. JScript gibi diller için derleyicileri yansıma sembol tabloları oluşturmak için kullanın. Sınıflarda <xref:System.Runtime.Serialization> ad alanı yansıma verilere erişmek ve kalıcı hale getirmek için hangi alanların belirlemek için kullanın. Sınıflarda <xref:System.Runtime.Remoting> ad alanı yansıma serileştirme üzerinden dolaylı olarak kullanın.  
  
## <a name="runtime-types-in-reflection"></a>Yansımadaki Çalışma Zamanı Türleri  
 Yansıma sağlayan sınıflar gibi <xref:System.Type> ve <xref:System.Reflection.MethodInfo>, türleri, üyeler, parametreleri ve diğer kodu varlıkları temsil etmek için. Ancak, doğrudan bu sınıflarla çalışmıyor yansıma kullandığınızda, hangi çoğunu soyut (`MustInherit` Visual Basic'te). Bunun yerine, ortak dil çalışma zamanı tarafından (CLR) sağlanan türleri ile çalışır.  
  
 Örneğin, kullandığınızda, C# `typeof` işleci (`GetType` Visual Basic'te) almak için bir <xref:System.Type> nesne, nesne türünde gerçekten bir `RuntimeType`. `RuntimeType`türetilen <xref:System.Type>ve uygulamaları soyut yöntemler sağlar.  
  
 Bu çalışma zamanı sınıflar `internal` (`Friend` Visual Basic'te). Davranışlarını temel sınıfın belgelerinde açıklanan çünkü bunlar ayrı olarak kendi temel sınıflarından açıklanmamıştır.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|Açıklar <xref:System.Type> sınıfı ve nasıl kullanılacağını gösteren kod örnekleri sağlar <xref:System.Type> Oluşturucular, yöntemleri, alanları, özellikleri ve olayları hakkında bilgi edinmek için birkaç yansıma sınıflarla.|  
|[Yansıma ve Genel Türler](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)|Tür parametreleri ve genel türler ve genel yöntemler tür bağımsız değişkenleri yansıma nasıl işleyeceğini açıklanmaktadır.|  
|[Yansımayla İlgili Güvenlik Konuları](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)|Ne derece yansıma türü bilgileri ve erişim türleri bulmak için kullanılabilecek belirleyen kuralları açıklar.|  
|[Türleri Dinamik Olarak Yükleme ve Kullanma](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)|Geç bağlama destekleyen yansıma özel bağlama arabirimi açıklanmaktadır.|  
|[Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Yalnızca yansıma yükleme bağlamı açıklar. Bağlam test etme ve bir derlemede salt yansıma bağlamına uygulanan öznitelikleri incelemek nasıl bir derlemeyi yüklemeye nasıl gösterir.|  
|[Özel Özniteliklere Erişim](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)|Yansıma sorgu özniteliği varlığı ve değerleri kullanarak gösterir.|  
|[Tam Olarak Nitelenmiş Tür Adlarını Belirtme](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)|Backus-Naur formu (BNF) ve özel karakterler, derleme adları, işaretçileri, başvuruları ve diziler belirtmek için gerekli sözdizimi bakımından tam olarak nitelenmiş tür adları biçimini tanımlar.|  
|[Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama](../../../docs/framework/reflection-and-codedom/how-to-hook-up-a-delegate-using-reflection.md)|Bir yöntem için temsilci oluşturun ve temsilci olaya kadar kanca açıklanmaktadır. Bir olay işleme yöntemi çalıştırma kullanarak nasıl oluşturulacağını açıklar <xref:System.Reflection.Emit.DynamicMethod>.|  
|[Dinamik Yöntemleri ve Derlemeleri Yayma](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Dinamik derlemeler ve dinamik yöntemleri oluşturmak açıklanmaktadır.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Type?displayProperty=nameWithType>  
  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
