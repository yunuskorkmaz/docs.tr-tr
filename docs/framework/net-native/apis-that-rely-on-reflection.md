---
title: Yansıma kullanan API'ler
ms.date: 03/30/2017
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
ms.openlocfilehash: 7329ac339912042fc5d2fb335faa3bf74ed03b8d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128536"
---
# <a name="apis-that-rely-on-reflection"></a>Yansıma kullanan API'ler
Bazı durumlarda, kodda yansıma kullanımı belirgin değildir ve bu nedenle .NET Native araç zinciri çalışma zamanında gereken meta verileri korumaz. Bu konu, yansıma API 'sinin bir parçası olarak kabul edilmeyen ancak yansıma dosyasını başarıyla yürütmek için kullanan bazı ortak API 'Leri veya ortak programlama düzenlerini ele almaktadır. Bunları kaynak kodunuzda kullanıyorsanız, bu API 'lere yapılan çağrıların bir [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumu veya çalışma zamanında başka bir özel durum oluşturmaması için çalışma zamanı yönergeleri (. RD. xml) dosyasına bunlarla ilgili bilgi ekleyebilirsiniz.  
  
## <a name="typemakegenerictype-method"></a>Type. MakeGenericType yöntemi  
 Aşağıdaki gibi bir kod kullanarak <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yöntemini çağırarak genel bir tür `AppClass<T>` dinamik olarak örnekleyebilirsiniz:  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Bu kodun çalışma zamanında başarılı olması için birkaç meta veri öğesi gereklidir. İlki, örneklenmemiş genel tür için `Browse` meta verilerdir, `AppClass<T>`:  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 Bu, <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> yöntemi çağrısının başarılı olmasını ve geçerli bir <xref:System.Type> nesnesi döndürmesini sağlar.  
  
 Ancak, örneklenmemiş genel tür için meta veriler eklediğinizde bile, <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yöntemini çağırmak bir [MissingMetadataException](missingmetadataexception-class-net-native.md) özel durumu oluşturur:  
  
Bu işlem, performans nedenleriyle aşağıdaki tür için meta veriler kaldırıldığından yürütülemiyor:  
  
`App1.AppClass`1 < System. Int32 > '.  
  
 <xref:System.Int32?displayProperty=nameWithType>`AppClass<T>` üzerine belirli bir örnek oluşturma için `Activate` meta verileri eklemek üzere çalışma zamanı yönergeleri dosyasına aşağıdaki çalışma zamanı yönergesini ekleyebilirsiniz:  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 `AppClass<T>` üzerinde her farklı örnekleme, <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yöntemiyle oluşturulduysa ve statik olarak kullanılmazsa ayrı bir yönerge gerektirir.  
  
## <a name="methodinfomakegenericmethod-method"></a>MethodInfo. MakeGenericMethod yöntemi  
 Bir sınıf `Class1` `GetMethod<T>(T t)`genel bir yöntem ile `GetMethod`, aşağıdaki gibi bir kod kullanılarak yansıma aracılığıyla çağrılabilir:  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Başarılı bir şekilde çalıştırmak için, bu kod birçok meta veri öğesi gerektirir:  
  
- yöntemi çağırmak istediğiniz türe ait meta verileri `Browse`.  
  
- çağırmak istediğiniz yöntem için meta verileri `Browse`.  Ortak bir yöntem ise, kapsayan tür için ortak `Browse` meta verileri eklemek de yöntemini içerir.  
  
- Çağırmak istediğiniz metodun dinamik meta verileri, böylece yansıma çağırma temsilcisi .NET Native araç zinciri tarafından kaldırılmaz. Yöntemi için dinamik meta veriler eksikse, <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> yöntemi çağrıldığında aşağıdaki özel durum oluşur:  
  
    ```output
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Aşağıdaki çalışma zamanı yönergeleri tüm gerekli meta verilerin kullanılabilir olduğundan emin olur:  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 Dinamik olarak çağrılan metodun her farklı örneklemesi için bir `MethodInstantiation` yönergesi gereklidir ve `Arguments` öğesi her farklı örnekleme bağımsız değişkenini yansıtacak şekilde güncelleştirilir.  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Array. CreateInstance ve Type. MakeTypeArray yöntemleri  
 Aşağıdaki örnek, bir tür `Class1`<xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> ve <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> yöntemlerini çağırır.  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Hiçbir dizi meta verisi yoksa, aşağıdaki hata oluşur:  
  
```output
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 dizi türü için `Browse` meta verileri dinamik olarak örneğini oluşturmak için gereklidir.  Aşağıdaki çalışma zamanı yönergesi `Class1[]`dinamik örneklemesini sağlar.  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Başlarken](getting-started-with-net-native.md)
- [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](runtime-directives-rd-xml-configuration-file-reference.md)
