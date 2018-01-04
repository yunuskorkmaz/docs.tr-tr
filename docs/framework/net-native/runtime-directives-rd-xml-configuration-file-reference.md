---
title: "Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8241523f-d8e1-4fb6-bf6a-b29bfe07b38a
caps.latest.revision: "27"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f452a32b209c30175f95aec7a8a90e0783c10086
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="runtime-directives-rdxml-configuration-file-reference"></a>Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu
Çalışma zamanı yönergeleri (. rd.xml) atanan program öğeleri yansıma için kullanılabilir olup olmadığını belirten bir XML yapılandırma dosyasını bir dosyadır. Aşağıda, bir çalışma zamanı yönergeleri dosyası örneği verilmiştir:  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
<Application>  
  <Namespace Name="Contoso.Cloud.AppServices" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.ViewModels" Serialize="Required Public" />  
  <Namespace Name="ContosoClient.DataModel" Serialize="Required Public" />  
  <Namespace Name="Contoso.Reader.UtilityLib" Serialize="Required Public" />  
  
  <Namespace Name="System.Collections.ObjectModel" >  
    <TypeInstantiation Name="ObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductItem" Serialize="Public" />  
    <TypeInstantiation Name="ReadOnlyObservableCollection"   
          Arguments="ContosoClient.DataModel.ProductGroup" Serialize="Public" />  
  </Namespace>  
</Application>  
</Directives>  
```  
  
## <a name="the-structure-of-a-runtime-directives-file"></a>Bir çalışma zamanı yönergeleri dosyasının yapısı  
 Çalışma zamanı yönergeleri kullanan dosya `http://schemas.microsoft.com/netfx/2013/01/metadata` ad alanı.  
  
 Kök öğe [yönergeleri](../../../docs/framework/net-native/directives-element-net-native.md) öğesi. Sıfır veya daha fazla içerebilir [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğeleri ve sıfır veya bir [uygulama](../../../docs/framework/net-native/application-element-net-native.md) aşağıdaki yapısında gösterildiği gibi öğesi. Özniteliklerini [uygulama](../../../docs/framework/net-native/application-element-net-native.md) öğesi, uygulama genelinde çalışma zamanı yansıma ilkesi tanımlayabilirsiniz ya da alt öğeleri için bir kapsayıcı olarak hizmet verebilir. [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğesi, diğer yandan, yalnızca bir kapsayıcıdır. Alt [uygulama](../../../docs/framework/net-native/application-element-net-native.md) ve [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğeleri türleri, yöntemleri, alanlar, özellikleri ve yansıma için kullanılabilir olan olayları tanımlayın.  
  
 Başvuru bilgileri için aşağıdaki yapısından öğeleri seçin veya bkz [çalışma zamanı yönerge öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md). Aşağıdaki hiyerarşi içinde üç nokta özyinelemeli yapısı işaretler. Bu öğe, isteğe bağlı veya gerekli olup olmadığı ve varsa kullanılır, bilgi köşeli gösterir (bir veya daha çok) kaç tane izin verilir.  
  
 [Yönergeleri](../../../docs/framework/net-native/directives-element-net-native.md) [1:1]  
 [Uygulama](../../../docs/framework/net-native/application-element-net-native.md) [0:1]  
 [Derleme](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 [Alt türleri](../../../docs/framework/net-native/subtypes-element-net-native.md) (kapsayan tür alt sınıflarının) [O:1]  
 [Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Attributeımplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (bir özniteliği olan türünü içeren) [O:1]  
 [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]  
 [Yöntem](../../../docs/framework/net-native/method-element-net-native.md) [0:M]  
 [Parametre](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]  
 [TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]  
 [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]  
 [Methodınstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (genel yöntem oluşturulan) [0:M]  
 [Özellik](../../../docs/framework/net-native/property-element-net-native.md) [0:M]  
 [Alan](../../../docs/framework/net-native/field-element-net-native.md) [0:M]  
 [Olay](../../../docs/framework/net-native/event-element-net-native.md) [0:M]  
 [Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]  
 [Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Yöntem](../../../docs/framework/net-native/method-element-net-native.md) [0:M]  
 [Parametre](../../../docs/framework/net-native/parameter-element-net-native.md) [0:M]  
 [TypeParameter](../../../docs/framework/net-native/typeparameter-element-net-native.md) [0:M]  
 [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]  
 [Methodınstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (genel yöntem oluşturulan) [0:M]  
 [Özellik](../../../docs/framework/net-native/property-element-net-native.md) [0:M]  
 [Alan](../../../docs/framework/net-native/field-element-net-native.md) [0:M]  
 [Olay](../../../docs/framework/net-native/event-element-net-native.md) [0:M]  
 [Kitaplık](../../../docs/framework/net-native/library-element-net-native.md) [0:M]  
 [Derleme](../../../docs/framework/net-native/assembly-element-net-native.md) [0:M]  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 [Alt türleri](../../../docs/framework/net-native/subtypes-element-net-native.md) (kapsayan tür alt sınıflarının) [O:1]  
 [Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Attributeımplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md) (bir özniteliği olan türünü içeren) [O:1]  
 [GenericParameter](../../../docs/framework/net-native/genericparameter-element-net-native.md) [0:M]  
 [Yöntem](../../../docs/framework/net-native/method-element-net-native.md) [0:M]  
 [Methodınstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (genel yöntem oluşturulan) [0:M]  
 [Özellik](../../../docs/framework/net-native/property-element-net-native.md) [0:M]  
 [Alan](../../../docs/framework/net-native/field-element-net-native.md) [0:M]  
 [Olay](../../../docs/framework/net-native/event-element-net-native.md) [0:M]  
 [Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]  
 [Tür](../../../docs/framework/net-native/type-element-net-native.md) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Typeınstantiation](../../../docs/framework/net-native/typeinstantiation-element-net-native.md) (genel tür oluşturulan) [0:M]  
 biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır. biçimindeki telefon numarasıdır.  
 [Yöntem](../../../docs/framework/net-native/method-element-net-native.md) [0:M]  
 [Methodınstantiation](../../../docs/framework/net-native/methodinstantiation-element-net-native.md) (genel yöntem oluşturulan) [0:M]  
 [Özellik](../../../docs/framework/net-native/property-element-net-native.md) [0:M]  
 [Alan](../../../docs/framework/net-native/field-element-net-native.md) [0:M]  
 [Olay](../../../docs/framework/net-native/event-element-net-native.md) [0:M]  
  
 [Uygulama](../../../docs/framework/net-native/application-element-net-native.md) öğesi özniteliklere sahip olabilir veya ele İlkesi özniteliklerini sağlayabilirsiniz [çalışma zamanı yönerge ve ilke bölümü](#Directives).  
  
 A [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğeye sahip tek bir öznitelik `Name`, bir kitaplık veya dosya uzantısı olmadan derleme adını belirtir. Örneğin, aşağıdaki [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) öğesi Extensions.dll adlı bir derleme için geçerlidir.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
  <Application>  
     <!-- Child elements go here -->    
  </Application>  
  <Library Name="Extensions">  
     <!-- Child elements go here -->    
  </Library>  
</Directives>  
```  
  
<a name="Directives"></a>   
## <a name="runtime-directives-and-policy"></a>Çalışma zamanı yönergeleri ve ilke  
 [Uygulama](../../../docs/framework/net-native/application-element-net-native.md) öğenin kendisi ve alt öğeleri [Kitaplığı](../../../docs/framework/net-native/library-element-net-native.md) ve [uygulama](../../../docs/framework/net-native/application-element-net-native.md) öğeleri express İlkesi; diğer bir deyişle, bunlar uygulama uygulayabileceğiniz biçimini tanımlayın Yansıma bir program öğesi için. İlke türü bir öğe özniteliği tarafından tanımlanan (örneğin, `Serialize`). Bir ilke değeri özniteliğinin değeri tarafından tanımlanır (örneğin, `Serialize="Required"`).  
  
 Bu ilke için bir değer belirtmezseniz tüm alt öğeleri öğenin bir özniteliği tarafından belirtilen herhangi bir ilke uygulanır. Örneğin, bir ilke tarafından belirtilen bir [türü](../../../docs/framework/net-native/type-element-net-native.md) içerdiği tüm türleri ve üyeleri için bir ilke açıkça belirtilmedi için ilke geçerli öğe.  
  
 Tarafından ifade İlkesi [uygulama](../../../docs/framework/net-native/application-element-net-native.md), [derleme](../../../docs/framework/net-native/assembly-element-net-native.md), [Attributeımplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [ Alt türleri](../../../docs/framework/net-native/subtypes-element-net-native.md), ve [türü](../../../docs/framework/net-native/type-element-net-native.md) öğeleri tek tek üyeleri için ifade İlkesi farklıdır (tarafından [yöntemi](../../../docs/framework/net-native/method-element-net-native.md), [özelliği](../../../docs/framework/net-native/property-element-net-native.md), [Alan](../../../docs/framework/net-native/field-element-net-native.md), ve [olay](../../../docs/framework/net-native/event-element-net-native.md) öğeleri).  
  
### <a name="specifying-policy-for-assemblies-namespaces-and-types"></a>Derlemeler, ad alanları ve türler için ilkesini belirtme  
 [Uygulama](../../../docs/framework/net-native/application-element-net-native.md), [derleme](../../../docs/framework/net-native/assembly-element-net-native.md), [Attributeımplies](../../../docs/framework/net-native/attributeimplies-element-net-native.md), [Namespace](../../../docs/framework/net-native/namespace-element-net-native.md), [Subtypes](../../../docs/framework/net-native/subtypes-element-net-native.md)ve [ Tür](../../../docs/framework/net-native/type-element-net-native.md) öğeleri aşağıdaki ilke türlerinden destekler:  
  
-   `Activate`. Örneklerinin etkinleştirmesi Oluşturucular, çalışma zamanı erişimi kontrol eder.  
  
-   `Browse`. Program öğeleri hakkında bilgi için sorgulama kontrol eder, ancak herhangi bir çalışma zamanı erişim sağlamaz.  
  
-   `Dynamic`. Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder.  
  
-   `Serialize`. Oluşturucular, alanları ve seri hale getirilmiş ve üçüncü taraf kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için özellikleri, çalışma zamanı erişimi denetler.  
  
-   `DataContractSerializer`. Denetimleri kullanan serileştirme için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.  
  
-   `DataContractJsonSerializer`. Denetimleri kullanan JSON serileştirmesi için ilke <xref:System.Runtime.Serialization.DataContractSerializer?displayProperty=nameWithType> sınıfı.  
  
-   `XmlSerializer`. Denetimleri kullanan XML serileştirme için ilke <xref:System.Xml.Serialization.XmlSerializer?displayProperty=nameWithType> sınıfı.  
  
-   `MarshalObject`. Başvuru türleri WinRT ve COM hazırlama için ilke denetler  
  
-   `MarshalDelegate`. Yerel kod için işlev işaretçileri olarak temsilci türleri hazırlama için ilke denetler.  
  
-   `MarshalStructure` . Yerel kod yapılara hazırlama için ilke denetler.  
  
 Bu ilke türleri ile ilişkili ayarları şunlardır:  
  
-   `All`. Tüm türleri ve araç zinciri kaldırmıyor üyeleri için ilkeyi etkinleştirin.  
  
-   `Auto`. Varsayılan davranışını kullanın. (Bir ilke belirtmeden Bu ilke ayarını için eşdeğer `Auto` Bu ilke, örneğin bir üst öğe tarafından geçersiz kılınmadığı sürece.)  
  
-   `Excluded`. Bir program öğesi için ilke devre dışı bırakın.  
  
-   `Public`. Araç zinciri üye gerekli değildir ve bu nedenle kaldırır belirler sürece genel türleri veya üyeleri için ilke etkinleştirin. (İkinci durumda, kullanmalısınız `Required Public` sağlamak üye tutulur ve yansıma özellikleri vardır.)  
  
-   `PublicAndInternal`. Araç zinciri bunları kaldırmaz, ortak ve iç türleri veya üyeleri için ilke etkinleştirin.  
  
-   `Required Public`. Genel türler ve desteklemediğini kullanılan üyeler tutmak için araç zinciri gerektirir ve bunlar için ilkeyi etkinleştirin.  
  
-   `Required PublicAndInternal`. Genel ve iç türleri ve desteklemediğini kullanılan üyeler tutmak için araç zinciri gerektirir ve bunlar için ilkeyi etkinleştirin.  
  
-   `Required All`. Tüm türleri ve desteklemediğini kullanılan üyeler tutmak için araç zinciri gerektirir ve bunlar için ilkeyi etkinleştirin.  
  
 Örneğin, şu çalışma zamanı yönergeleri dosya İlkesi tüm türleri ve üyeleri için derleme DataClasses.dll tanımlar. Tüm ortak özellikler, tüm türleri ve tür üyeleri için gözatma etkinleştirir serileştirmek tüm türler için etkinleştirme sağlar yansıma sağlar (nedeniyle `Dynamic` özniteliği) ve yansıma tüm genel türleri ve üyeleri için etkinleştirir.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"   
                Browse="All" Activate="PublicAndInternal"   
                Dynamic="Public"  />  
   </Application>  
   <Library Name="UtilityLibrary">  
     <!-- Child elements go here -->    
   </Library>  
</Directives>  
```  
  
### <a name="specifying-policy-for-members"></a>Üyeler için ilkesini belirtme  
 [Özelliği](../../../docs/framework/net-native/property-element-net-native.md) ve [alan](../../../docs/framework/net-native/field-element-net-native.md) öğeleri aşağıdaki ilke türlerinden destekler:  
  
-   `Browse`-Denetimleri bu üye hakkında bilgi için sorgulama ancak herhangi bir çalışma zamanı erişim sağlamaz.  
  
-   `Dynamic`-Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder. Ayrıca, kapsayan tür hakkında bilgi için sorgulama denetler.  
  
-   `Serialize`-Sıralanabilir ve kitaplıklar gibi Newtonsoft JSON seri hale getirici tarafından seri türü örnekleri etkinleştirmek için üye çalışma zamanı erişimi kontrol eder. Bu ilke, Oluşturucular, alanlar ve özellikler için uygulanabilir.  
  
 [Yöntemi](../../../docs/framework/net-native/method-element-net-native.md) ve [olay](../../../docs/framework/net-native/event-element-net-native.md) öğeleri aşağıdaki ilke türlerinden destekler:  
  
-   `Browse`-Denetimleri bu üye hakkında bilgi için sorgulama ancak herhangi bir çalışma zamanı erişim sağlamaz.  
  
-   `Dynamic`-Dinamik programlama etkinleştirmek için Oluşturucular, yöntemleri, alanları, özellikleri ve olayları dahil tüm tür üyeleri, çalışma zamanı erişimi kontrol eder. Ayrıca, kapsayan tür hakkında bilgi için sorgulama denetler.  
  
 Bu ilke türleri ile ilişkili ayarları şunlardır:  
  
-   `Auto`-Varsayılan davranışını kullanın. (Bir ilke belirtmeden Bu ilke ayarını için eşdeğer `Auto` bir şey geçersiz kılmadıkça.)  
  
-   `Excluded`-Hiç üye için meta verileri içerir.  
  
-   `Included`-Üst tür çıktıda varsa, ilke etkinleştirin.  
  
-   `Required`-Bu üye tutmak için araç zinciri gerektiren bile görünüyor kullanılmayan ve ilke için etkinleştirin.  
  
## <a name="runtime-directives-file-semantics"></a>Çalışma zamanı yönergeleri dosya semantiği  
 İlke için üst düzey ve alt düzey öğeleri eşzamanlı olarak tanımlanabilir. Örneğin, ilke bir derlemenin ve bu derleme içinde yer alan türlerinden bazıları için tanımlanabilir. Belirli bir alt düzey öğesinin temsil edilmeyen, kendi üst ilkesini devralır. Örneğin, varsa bir `Assembly` öğe varsa ancak `Type` öğeleri olmayan, ilke içinde belirtilen `Assembly` derlemesinde her türünü öğesi uygulanır. Birden çok öğe aynı program öğesi için ilke geçerli olabilir. Örneğin, ayrı [derleme](../../../docs/framework/net-native/assembly-element-net-native.md) öğeleri tanımlamak aynı ilke öğesi için aynı bütünleştirilmiş kodda farklı. Aşağıdaki bölümler, belirli bir tür için ilke bu gibi durumlarda nasıl çözümleneceğini açıklar.  
  
 A [türü](../../../docs/framework/net-native/type-element-net-native.md) veya [yöntemi](../../../docs/framework/net-native/method-element-net-native.md) öğesi genel türü veya yöntemi kendi ilke olmayan tüm örneklemesi kendi ilke uygulanır. Örneğin, bir `Type` ilkesini belirtir öğesi <xref:System.Collections.Generic.List%601> belirli bir genel tür oluşturulan için kılınmadığı sürece genel bu türdeki tüm oluşturulan örnekleri için geçerlidir (gibi bir `List<Int32>`) tarafından bir `TypeInstantiation` öğesi. Aksi takdirde, öğeleri adlı bir program öğesi için bir ilke tanımlayın.  
  
 Bir öğenin belirsiz olduğunda, altyapı eşleşmeleri arar ve tam bir eşleşme bulursa, onu kullanır. Birden çok eşleşme bulursa, bir uyarı veya hata olmayacaktır.  
  
### <a name="if-two-directives-apply-policy-to-the-same-program-element"></a>İki yönergeleri aynı program öğesi için ilke uygularsanız  
 Farklı çalışma zamanı yönergeleri dosyalarındaki iki öğe aynı ilke türü (örneğin, bir derleme veya tür) aynı program öğesi için farklı bir değere ayarlamaya çalışırsanız, çakışma gibi çözümlendi:  
  
1.  Varsa `Excluded` öğesi mevcutsa, önceliğe sahiptir.  
  
2.  `Required`önceliğe sahip üstünde değil `Required`.  
  
3.  `All`üzerinden önceliğe sahip `PublicAndInternal`, üzerinden önceliği olan `Public`.  
  
4.  Açık herhangi bir ayar üzerinden önceliğe sahip `Auto`.  
  
 Tek bir proje aşağıdaki iki çalışma zamanı yönergeleri dosyalar içeriyorsa, örneğin, serileştirme ilke DataClasses.dll için her iki ayarlanmışsa `Required Public` ve `All`. Bu durumda, serileştirme ilke olarak çözümlenmiş olacaktır `Required All`.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public"/>  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="All" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
 Ancak, bir tek çalışma zamanı yönergeleri dosyasında iki yönergeleri aynı program öğesi için aynı ilke türü ayarlamaya çalışırsanız, XML Şeması tanımı aracı bir hata iletisi görüntüler.  
  
### <a name="if-child-and-parent-elements-apply-the-same-policy-type"></a>Alt ve üst öğeleri aynı ilke türü uygularsanız  
 Alt öğeler de dahil olmak üzere kendi üst öğeler geçersiz kılma `Excluded` ayarı. Geçersiz kılma olduğunu belirtmek için isteyeceğiniz ana nedeni `Auto`.  
  
 Aşağıdaki örnekte, her şeyi için seri hale getirme ilkesini `DataClasses` olmayan içinde `DataClasses.ViewModels` olacaktır `Required Public`ve ikisi de olan her şeyi `DataClasses` ve `DataClasses.ViewModels` olacaktır `All`.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
   </Appliction>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="if-open-generics-and-instantiated-elements-apply-the-same-policy-type"></a>Açık genel türler ve oluşturulan öğeleri aynı ilke türü uygulanacaksa  
 Aşağıdaki örnekte, `Dictionary<int,int>` atanan `Browse` yalnızca altyapısı onu vermek için başka bir neden varsa İlkesi `Browse` (Aksi takdirde varsayılan davranışı olur) ilkesini; sayısı her bir örneklemesi <xref:System.Collections.Generic.Dictionary%602> sahip olur üyeleri göz atılamaz.  
  
```xml  
<Directives xmlns="http://schemas.microsoft.com/netfx/2013/01/metadata">  
   <Application>  
      <Assembly Name="DataClasses" Serialize="Required Public" >  
         <Namespace Name="DataClasses.ViewModels" Seralize="All" />  
      </Assembly>  
      <Namespace Name="DataClasses.Generics" />  
      <Type Name="Dictionary" Browse="All" />  
      <TypeInstantiation Name="Dictionary"   
                         Arguments="System.Int32,System.Int32" Browse="Auto" />  
   </Application>  
   <Library Name="DataClasses">  
      <!-- any other elements -->  
   </Library>  
</Directives>  
```  
  
### <a name="how-policy-is-inferred"></a>İlke nasıl algılanır  
 Her ilke türünün farklı bir diğer yapıların Bu ilke türü varlığını nasıl etkilediğini belirlemek kural kümesi vardır.  
  
#### <a name="the-effect-of-browse-policy"></a>Gözat ilkesinin etkisini  
 Uygulama `Browse` ilke türü için aşağıdaki ilke değişiklikleri içerir:  
  
-   Türünün temel türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Bir oluşturulmuş genel türündeyse türü dizilerine sürümü ile işaretlenmiş `Browse` ilkesi.  
  
-   Türü bir delegate ise `Invoke` türünün yöntemi ile işaretlenmiş `Dynamic` ilkesi.  
  
-   Her bir arabirime türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Türü için uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Tür genel ise, her kısıtlama türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Tür genel ise, türü örneği türleri ile işaretlenmiş `Browse` ilkesi.  
  
 Uygulama `Browse` ilke için bir yöntem aşağıdaki ilke değişiklikleri içerir:  
  
-   Yöntem her parametre türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Yöntemin dönüş türünü işaretlenmiş `Browse` ilkesi.  
  
-   Yöntem içeren tür ile işaretlenmiş `Browse` ilkesi.  
  
-   Yöntemi bir oluşturulmuş genel yöntem ise, dizilerine genel yöntem ile işaretlenmiş `Browse` ilkesi.  
  
-   Yöntemine uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Metodu genel ise, her kısıtlama türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Metodu genel ise, yöntemi örneği türleri ile işaretlenir `Browse` ilkesi.  
  
 Uygulama `Browse` bir alana ilke aşağıdaki ilke değişiklikleri içerir:  
  
-   Alana uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Alanın türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Alanın ait olduğu tür ile işaretlenmiş `Browse` ilkesi.  
  
#### <a name="the-effect-of-dynamic-policy"></a>Dinamik ilkesinin etkisini  
 Uygulama `Dynamic` ilke türü için aşağıdaki ilke değişiklikleri içerir:  
  
-   Türünün temel türü ile işaretlenmiş `Dynamic` ilkesi.  
  
-   Bir oluşturulmuş genel türündeyse türü dizilerine sürümü ile işaretlenmiş `Dynamic` ilkesi.  
  
-   Tür bir temsilci türü ise `Invoke` türünün yöntemi ile işaretlenmiş `Dynamic` ilkesi.  
  
-   Her bir arabirime türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Türü için uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Tür genel ise, her kısıtlama türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Tür genel ise, türü örneği türleri ile işaretlenmiş `Browse` ilkesi.  
  
 Uygulama `Dynamic` ilke için bir yöntem aşağıdaki ilke değişiklikleri içerir:  
  
-   Yöntem her parametre türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Yöntemin dönüş türünü işaretlenmiş `Dynamic` ilkesi.  
  
-   Yöntem içeren tür ile işaretlenmiş `Dynamic` ilkesi.  
  
-   Yöntemi bir oluşturulmuş genel yöntem ise, dizilerine genel yöntem ile işaretlenmiş `Browse` ilkesi.  
  
-   Yöntemine uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Metodu genel ise, her kısıtlama türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Metodu genel ise, yöntemi örneği türleri ile işaretlenir `Browse` ilkesi.  
  
-   Yöntemi tarafından çağrılan `MethodInfo.Invoke`, ve temsilci oluşturma tarafından mümkün hale <xref:System.Reflection.MethodInfo.CreateDelegate%2A?displayProperty=nameWithType>.  
  
 Uygulama `Dynamic` bir alana ilke aşağıdaki ilke değişiklikleri içerir:  
  
-   Alana uygulanan her bir öznitelik türü ile işaretlenmiş `Browse` ilkesi.  
  
-   Alanın türü ile işaretlenmiş `Dynamic` ilkesi.  
  
-   Alanın ait olduğu tür ile işaretlenmiş `Dynamic` ilkesi.  
  
#### <a name="the-effect-of-activation-policy"></a>Etkinleştirme ilkesinin etkisini  
 Bir türe etkinleştirme İlkesi uygulama aşağıdaki ilke değişiklikleri içerir:  
  
-   Bir oluşturulmuş genel türündeyse türü dizilerine sürümü ile işaretlenmiş `Browse` ilkesi.  
  
-   Tür bir temsilci türü ise `Invoke` türünün yöntemi ile işaretlenmiş `Dynamic` ilkesi.  
  
-   Oluşturucular türü ile işaretlenmiş `Activation` ilkesi.  
  
 Uygulama `Activation` ilke için bir yöntem aşağıdaki ilke değişikliğini içerir:  
  
-   Oluşturucusu tarafından çağrılan <xref:System.Reflection.ConstructorInfo.Invoke%2A?displayProperty=nameWithType> ve <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> yöntemleri. Yöntemleri için `Activation` ilke yalnızca oluşturucular etkiler.  
  
 Uygulama `Activation` bir alana İlkesi etkisi yoktur.  
  
#### <a name="the-effect-of-serialize-policy"></a>Serileştirme ilkesinin etkisini  
 `Serialize` İlkesi ortak yansıma tabanlı serileştiricileri kullanımını etkinleştirir. Ancak, Microsoft dışı serileştiricileri tam yansıma erişim desenlerini Microsoft'a bilinmiyor olduğundan, bu ilkeyi tamamen etkili olmayabilir.  
  
 Uygulama `Serialize` ilke türü için aşağıdaki ilke değişiklikleri içerir:  
  
-   Türünün temel türü ile işaretlenmiş `Serialize` ilkesi.  
  
-   Bir oluşturulmuş genel türündeyse türü dizilerine sürümü ile işaretlenmiş `Browse` ilkesi.  
  
-   Tür bir temsilci türü ise `Invoke` türünün yöntemi ile işaretlenmiş `Dynamic` ilkesi.  
  
-   Bir numaralandırma türü ise, bir dizi türü ile işaretlenmiş `Serialize` ilkesi.  
  
-   Türü uyguluyorsa <xref:System.Collections.Generic.IEnumerable%601>, `T` ile işaretlenen `Serialize` ilkesi.  
  
-   Tür ise <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.Generic.IList%601>, <xref:System.Collections.Generic.ICollection%601>, <xref:System.Collections.Generic.IReadOnlyCollection%601>, veya <xref:System.Collections.Generic.IReadOnlyList%601>, ardından `T[]` ve <xref:System.Collections.Generic.List%601> ile işaretlenen `Serialize` ilkenin ancak hiçbir arabirim türü üyeleri ileişaretlenmiş`Serialize`ilkesi.  
  
-   Tür ise <xref:System.Collections.Generic.List%601>, hiçbir üye türü işaretlenir `Serialize` ilkesi.  
  
-   Tür ise <xref:System.Collections.Generic.IDictionary%602>, <xref:System.Collections.Generic.Dictionary%602> ile işaretlenen `Serialize` ilkesi. ancak hiçbir üye türü işaretlenir `Serialize` ilkesi.  
  
-   Tür ise <xref:System.Collections.Generic.Dictionary%602>, hiçbir üye türü işaretlenir `Serialize` ilkesi.  
  
-   Türü uyguluyorsa <xref:System.Collections.Generic.IDictionary%602>, `TKey` ve `TValue` işaretlenir `Serialize` ilkesi.  
  
-   Her oluşturucusu, her özellik erişimcisini ve her bir alan ile işaretlenmiş `Serialize` ilkesi.  
  
 Uygulama `Serialize` ilke için bir yöntem aşağıdaki ilke değişiklikleri içerir:  
  
-   İçeren türü ile işaretlenmiş `Serialize` ilkesi.  
  
-   Yöntemin dönüş türünü işaretlenmiş `Serialize` ilkesi.  
  
 Uygulama `Serialize` bir alana ilke aşağıdaki ilke değişiklikleri içerir:  
  
-   İçeren türü ile işaretlenmiş `Serialize` ilkesi.  
  
-   Alanın türü ile işaretlenmiş `Serialize` ilkesi.  
  
#### <a name="the-effect-of-xmlserializer-datacontractserializer-and-datacontractjsonserialier-policies"></a>XmlSerializer, DataContractSerializer ve DataContractJsonSerialier ilkelerinin etkisini  
 Aksine `Serialize` yansıma tabanlı serileştiricileri için tasarlanmıştır, ilke `XmlSerializer`, `DataContractSerializer`, ve `DataContractJsonSerializer` bilinen serileştiricileri kümesi etkinleştirmek için kullanılan ilkeleri [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri. Yansıma kullanarak bu serileştiricileri uygulanmaz, ancak çalışma zamanında seri hale getirilebilir türler kümesi benzer bir şekilde reflectable türleri olarak belirlenir.  
  
 Bu ilkeler birini türüne uygulama türü ile eşleşen seri hale getirici serileştirilmesi etkinleştirir. Ayrıca, serileştirme motoruna statik olarak serileştirme gerek olarak belirleyebilirsiniz türleri de seri hale getirilebilir.  
  
 Bu ilkeler yöntemleri veya alanlar üzerinde hiçbir etkisi yoktur.  
  
 Daha fazla bilgi için "Serileştiricileri farklar" bölümüne bakın [geçirme Windows mağazası uygulamanızı .NET yerele](../../../docs/framework/net-native/migrating-your-windows-store-app-to-net-native.md).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çalışma Zamanı Yönerge Öğeleri](../../../docs/framework/net-native/runtime-directive-elements.md)  
 [Yansıma ve .NET Native](../../../docs/framework/net-native/reflection-and-net-native.md)
