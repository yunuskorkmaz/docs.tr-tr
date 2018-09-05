---
title: .NET Framework'te Yansıma
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6a03e6760fbb233c656909fb99b48a84bddedef8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43509028"
---
# <a name="reflection-in-the-net-framework"></a>.NET Framework'te Yansıma
Sınıflarda <xref:System.Reflection> ad alanı, birlikte <xref:System.Type?displayProperty=nameWithType>, yüklenen hakkında bilgi edinmek etkinleştirdiğiniz [derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) ve gibi bunlar dahilinde tanımlanan türler [sınıfları](https://msdn.microsoft.com/library/ad7d3561-271e-4546-82fc-e00b059f27a9), [arabirimleri](https://msdn.microsoft.com/library/fd9d5975-5363-4bc9-b883-609f887895e5), ve [değer türleri](https://msdn.microsoft.com/library/c9c567f8-8ab1-4d88-834d-00f7d92418de). Yansıma, çalışma zamanında tür örnekleri oluşturma ve çağırma ve bunlara erişmek için de kullanabilirsiniz. Yansıma belirli yönleri hakkında konular için bkz [ilgili konular](#related_topics) sonunda, bu genel bakış.  
  
 [Ortak dil çalışma zamanı](../../../docs/standard/clr.md) yükleyici yönetir [uygulama etki alanları](../../../docs/framework/app-domains/application-domains.md), aynı uygulama kapsamı olan nesnelerin etrafında sınırları tanımlanmış hangi oluşturur. Bu yönetim uygun uygulama etki alanına her derlemenin yüklenmesi ve her bir derleme içinde tür hiyerarşisi bellek düzenini denetleme içerir.  
  
 [Derlemeleri](../../../docs/framework/app-domains/assemblies-in-the-common-language-runtime.md) türü üyeleri içeren modüller içerir ve modülleri türleri içerir. Yansıma, derlemeler, modüller ve türler yalıtan nesneleri sağlar. Yansıma, dinamik olarak bir türün bir örneğini oluşturma, bağlama türü var olan bir nesneye veya mevcut bir nesneden türü almak için kullanabilirsiniz. Ardından, türün yöntemlerini çağırmak veya kendi alanlarına ve özelliklerine erişebilirsiniz. Yansıma tipik kullanımları şunlardır:  
  
-   Kullanım <xref:System.Reflection.Assembly> tanımlamak ve derlemeler yüklemek için derleme bildiriminde listelenen, bu derlemedeki bir türünü bulun ve bir örneğini oluşturmak modülleri yükleme.  
  
-   Kullanım <xref:System.Reflection.Module> modülü ve modülde sınıfları içeren derleme gibi bilgileri bulmak için. Ayrıca, tüm genel yöntemler veya modülde tanımlanan diğer belirli, Global olmayan yöntemler de alabilirsiniz.  
  
-   Kullanım <xref:System.Reflection.ConstructorInfo> adı, parametreleri gibi bilgileri bulmak için erişim değiştiricilerine (gibi `public` veya `private`) ve uygulama ayrıntılarını (gibi `abstract` veya `virtual`) bir oluşturucu. Kullanım <xref:System.Type.GetConstructors%2A> veya <xref:System.Type.GetConstructor%2A> yöntemi bir <xref:System.Type> belirli bir oluşturucuyu çağırmak için.  
  
-   Kullanım <xref:System.Reflection.MethodInfo> adı gibi bilgileri bulmak için dönüş türü, parametreleri, erişim değiştiricileri (gibi `public` veya `private`) ve uygulama ayrıntılarını (gibi `abstract` veya `virtual`) yöntemi. Kullanım <xref:System.Type.GetMethods%2A> veya <xref:System.Type.GetMethod%2A> yöntemi bir <xref:System.Type> belirli bir yöntemi çağırmak için.  
  
-   Kullanım <xref:System.Reflection.FieldInfo> adı gibi bilgileri bulmak için erişim değiştiricileri (gibi `public` veya `private`) ve uygulama ayrıntılarını (gibi `static`), bir alanın ve almak veya alan değerlerini ayarlamak için.  
  
-   Kullanım <xref:System.Reflection.EventInfo> ad, olay işleyici veri türü, özel öznitelikler, türü ve bir olayın yansıtılan türü bildirme gibi bilgileri bulmak ve eklemek veya olay işleyicilerini kaldırmak için.  
  
-   Kullanım <xref:System.Reflection.PropertyInfo> adı gibi bilgileri bulmak için türü, veri türü, türü bildirmek yansıtılır ve bir özelliğin ve almak veya özellik değerlerini ayarlamak için salt okunur veya yazılabilir durumu.  
  
-   Kullanım <xref:System.Reflection.ParameterInfo> bir parametrenin adı gibi bilgileri bulmak için veri türü, bir giriş veya çıkış parametresi ve parametre konumunu bir yöntem imzası bir parametre olup olmadığını.  
  
-   Kullanım <xref:System.Reflection.CustomAttributeData> uygulama etki alanı salt yansıma bağlamında çalışırken özel öznitelikler hakkında bilgi bulmak için. <xref:System.Reflection.CustomAttributeData> bunları örneklerini oluşturmaya gerek kalmadan öznitelikleri incelemenize olanak sağlar.  
  
 Sınıflarını <xref:System.Reflection.Emit> ad alanı, çalışma zamanında türleri oluşturmanıza olanak sağlayan bir yansıma özel biçimi sağlayın.  
  
 Yansıma türlerini seçin ve ardından bu türleri hakkındaki bilgileri görüntülemek kullanıcıların türü tarayıcılar adlı uygulamalar oluşturmak için de kullanılabilir.  
  
 Diğer kullanımlar için yansıma vardır. JScript gibi diller System.codeDom yansıma sembol tabloları oluşturmak için kullanın. Sınıflarda <xref:System.Runtime.Serialization> ad alanı, yansıma verilere erişmek ve kalıcı hale getirmek için hangi alanları belirlemek için kullanın. Sınıflarda <xref:System.Runtime.Remoting> ad alanı, yansıma seri hale getirme yoluyla dolaylı olarak kullanın.  
  
## <a name="runtime-types-in-reflection"></a>Yansımadaki Çalışma Zamanı Türleri  
 Yansıma sınıfları gibi sağlar <xref:System.Type> ve <xref:System.Reflection.MethodInfo>, türleri, üyeler, parametreleri ve diğer kod varlıkları temsil etmek için. Ancak, doğrudan bu sınıflarla çalışmıyor yansıma kullandığınızda çoğunu soyut (`MustInherit` Visual Basic'te). Bunun yerine, ortak dil çalışma (CLR) tarafından sağlanan türleri ile çalışır.  
  
 Örneğin, kullandığınızda, C# `typeof` işleci (`GetType` Visual Basic'te) almak için bir <xref:System.Type> nesnesi, nesne gerçekten bir `RuntimeType`. `RuntimeType` öğesinden türetilen <xref:System.Type>ve uygulamalarını tüm soyut yöntemler sağlar.  
  
 Bu çalışma zamanı sınıflar `internal` (`Friend` Visual Basic'te). Davranışlarını temel sınıf belgelerinde açıklanan çünkü bunlar ayrı olarak kendi temel sınıflarından belgelenmemiştir.  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>İlgili Konular  
  
|Başlık|Açıklama|  
|-----------|-----------------|  
|[Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)|Açıklar <xref:System.Type> sınıfı ve nasıl kullanılacağını örneklendiren kod örnekleri sağlar <xref:System.Type> Oluşturucular, yöntemler, alanlar, özellikler ve olaylar hakkında bilgi edinmek için birkaç yansıma sınıfları ile.|  
|[Yansıma ve Genel Türler](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)|Yansıma tür parametreleri ve genel türler ve genel metotlar tür bağımsız değişkenleri nasıl işlediğini açıklar.|  
|[Yansımayla İlgili Güvenlik Konuları](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)|Tür bilgilerini ve erişim türleri bulmak için yansıtma ne derece kullanılabileceğini belirleyen kurallar açıklanmaktadır.|  
|[Türleri Dinamik Olarak Yükleme ve Kullanma](../../../docs/framework/reflection-and-codedom/dynamically-loading-and-using-types.md)|Geç bağlama destekleyen yansıma özel bağlama arabiriminde açıklar.|  
|[Nasıl yapılır: Salt Yansıma Bağlamına Derlemeleri Yükleme](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md)|Yalnızca yansıma yükleme bağlamı tanımlar. Bir derlemeyi yüklemek nasıl bağlamı test etme ve İnceleme salt yansıma bağlamında bir derlemeye uygulanan öznitelikleri gösterir.|  
|[Özel Özniteliklere Erişim](../../../docs/framework/reflection-and-codedom/accessing-custom-attributes.md)|Yansıma sorgu öznitelik varlığı ve değerleri kullanmayı gösterir.|  
|[Tam Olarak Nitelenmiş Tür Adlarını Belirtme](../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md)|Backus-Naur form (BNF) ve özel karakterler, derleme adları, işaretçiler, başvurular ve diziler belirtmek için gereken söz dizimi bakımından tam olarak nitelenmiş tür adlarını biçimini tanımlar.|  
|[Nasıl yapılır: Yansıma Kullanarak Temsilci Bağlama](../../../docs/framework/reflection-and-codedom/how-to-hook-up-a-delegate-using-reflection.md)|Bir yöntem için temsilci oluşturmak ve temsilci bir olay kadar kanca açıklanmaktadır. Bir olay işleme yöntemi kullanarak çalışma zamanı oluşturma açıklanır <xref:System.Reflection.Emit.DynamicMethod>.|  
|[Dinamik Yöntemleri ve Derlemeleri Yayma](../../../docs/framework/reflection-and-codedom/emitting-dynamic-methods-and-assemblies.md)|Dinamik derlemeler ve dinamik yöntemler oluşturma adımları açıklanmaktadır.|  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Type?displayProperty=nameWithType>  
  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
