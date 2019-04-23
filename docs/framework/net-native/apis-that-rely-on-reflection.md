---
title: Yansıma kullanan API'ler
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e7ec1280f3b7ba25367fac21d5160046915636a5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59076867"
---
# <a name="apis-that-rely-on-reflection"></a>Yansıma kullanan API'ler
Bazı durumlarda, kodda yansıma kullanımına açıktır, değildir ve bu nedenle [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri, çalışma zamanında gereken meta verileri korumak değil. Bu konu, bazı ortak API'ler veya, yansıma API'si bir parçası olarak kabul değildir ancak, başarılı bir şekilde yürütmek için yansıma kullanan ortak programlama modellerini kapsar. Kaynak kodunuzu kullanmak, bunlar hakkında bilgi için çalışma zamanı yönergeleri ekleyebilirsiniz (. rd.xml) bu API'lere giden çağrıların değil throw dosyasını bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durum ya da diğer bazı özel çalışma zamanında.  
  
## <a name="typemakegenerictype-method"></a>Type.MakeGenericType yöntemi  
 Dinamik olarak bir genel tür örneği oluşturabilir `AppClass<T>` çağırarak <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> aşağıdakine benzer bir kod kullanarak yöntemi:  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Çeşitli meta veri öğelerinin çalışma zamanında başarılı olması bu kod için gereklidir. İlk `Browse` örneklenmemiş genel türü için meta verileri `AppClass<T>`:  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 Böylece <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> metot çağrısı başarılı olması ve geçerli bir döndürmek için <xref:System.Type> nesne.  
  
 Ancak bile örneklenmemiş genel türü için meta verileri eklediğinizde, çağırma <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yöntem bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durum:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 Çalışma zamanı yönergeleri dosyasına eklemek için aşağıdaki çalışma zamanı yönerge ekleyebilirsiniz `Activate` belirli örneklemesi için meta verileri `AppClass<T>` , <xref:System.Int32?displayProperty=nameWithType>:  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 Üzerinden farklı her örneklemesi `AppClass<T>` ayrı yönergesi ile oluşturuluyorsa gerektirir <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yöntemi ve statik olarak kullanılmaz.  
  
## <a name="methodinfomakegenericmethod-method"></a>MethodInfo.MakeGenericMethod yöntemi  
 Bir sınıf verilen `Class1` ile genel yöntem `GetMethod<T>(T t)`, `GetMethod` yansıma yoluyla bu kodu kullanarak çağrılabilir:  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Başarılı bir şekilde çalıştırmak için bu kodu çeşitli meta veri öğeleri gerektirir:  
  
-   `Browse` yöntem çağırmak istediğinizde türü için meta veriler.  
  
-   `Browse` aramak istediğiniz yöntem için meta veriler.  Genel bir yöntem ise, genel ekleme `Browse` kapsayan türü için meta verileri yöntemi çok içerir.  
  
-   Dinamik meta veriler, istediğiniz çağırmak için böylece yansıma çağırma temsilcisi tarafından kaldırılmaz yöntemi [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri. Dinamik meta veriler için yöntem eksikse, şu özel durum oluşan <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> yöntemi çağrılır:  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Aşağıdaki çalışma zamanı yönergeleri gerekli tüm meta veriler kullanılabilir olduğundan emin olun:  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 A `MethodInstantiation` yönergesi her farklı örneğinin dinamik olarak çağrılan yöntem için gereklidir ve `Arguments` öğesi her farklı örneklemesine değişken yansıtacak şekilde güncelleştirilir.  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Array.CreateInstance ve Type.MakeTypeArray yöntemleri  
 Aşağıdaki örnek çağrıları <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> ve <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> bir türündeki yöntemlere `Class1`.  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Dizi meta veri işlemi varsa, aşağıdaki hata oluşur:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 `Browse` dizi türü için meta verilerini dinamik olarak oluşturmak için gereklidir.  Dinamik örneklemesi aşağıdaki çalışma zamanı yönerge sağlar `Class1[]`.  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
