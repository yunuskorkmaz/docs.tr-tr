---
title: Yansıma kullanan API'ler
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9532629-6594-4a41-909f-d083f30a42f3
caps.latest.revision: ''
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 49ac12bcae3fd85744961a6e3b81129178c2c323
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/26/2018
---
# <a name="apis-that-rely-on-reflection"></a>Yansıma kullanan API'ler
Bazı durumlarda, kodda yansıma kullanımına açıktır, değil ve bu nedenle [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri çalışma zamanında gereken meta verileri korumak değil. Bu konu, bazı ortak API'ler veya, API yansıma bir parçası olarak kabul değil ancak başarıyla yürütme yansıma kullanan ortak programlama desenleri kapsar. Bunları kaynak kodunda kullanırsanız, bunlar hakkında bilgi için çalışma zamanı yönergeleri ekleyebilirsiniz (. rd.xml) Bu API çağrıları değil throw dosyasını bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durumu veya çalışma zamanında diğer bazı bir özel durum.  
  
## <a name="typemakegenerictype-method"></a>Type.MakeGenericType yöntemi  
 Genel bir tür dinamik olarak oluşturabileceğiniz `AppClass<T>` çağırarak <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> aşağıdakine benzer bir kod kullanarak yöntemi:  
  
 [!code-csharp[ProjectN#1](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/type_makegenerictype1.cs#1)]  
  
 Bu kod çalışma zamanında başarılı olması çeşitli öğeleri meta verilerin gereklidir. İlk `Browse` dizilerine genel türü için meta veri `AppClass<T>`:  
  
```xml  
<Type Name="App1.AppClass`1" Browse="Required PublicAndInternal" />  
```  
  
 Böylece <xref:System.Type.GetType%28System.String%2CSystem.Boolean%29?displayProperty=nameWithType> başarılı ve geçerli bir dönmek için yöntem çağrısı <xref:System.Type> nesnesi.  
  
 Ancak bile dizilerine genel türü için meta veri eklediğinizde çağırma <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yöntemi atar bir [MissingMetadataException](../../../docs/framework/net-native/missingmetadataexception-class-net-native.md) özel durum:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.AppClass`1<System.Int32>.  
```  
  
 Aşağıdaki çalışma zamanı yönergesi eklemek için çalışma zamanı yönergeleri dosyasına ekleyebilirsiniz `Activate` belirli örnek oluşturma için meta verileri `AppClass<T>` , <xref:System.Int32?displayProperty=nameWithType>:  
  
```xml  
<TypeInstantiation Name="App1.AppClass" Arguments="System.Int32"   
                   Activate="Required Public" />  
```  
  
 Her farklı örneklemesi üzerinden `AppClass<T>` ile oluşturulduysa ayrı bir yönerge gerektirir <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> yöntemi ve statik olarak kullanılmaz.  
  
## <a name="methodinfomakegenericmethod-method"></a>MethodInfo.MakeGenericMethod yöntemi  
 Bir sınıf verilen `Class1` bir genel yöntem `GetMethod<T>(T t)`, `GetMethod` aşağıdakine benzer bir kod kullanarak yansıma yoluyla çağrılabilir:  
  
 [!code-csharp[ProjectN#2](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/makegenericmethod1.cs#2)]  
  
 Başarılı bir şekilde çalıştırmak için bu kodu meta verilerin çeşitli öğeleri gerektirir:  
  
-   `Browse` yöntem aramak istediğiniz türü için meta veriler.  
  
-   `Browse` aramak istediğiniz yöntemi için meta veriler.  Genel yöntem olması durumunda, ortak ekleme `Browse` içeren türü için meta verileri yöntemi çok içerir.  
  
-   İstediğiniz çağırmak için böylece yansıma çağırma temsilcisi tarafından kaldırılmaz yöntemi için dinamik meta verileri [!INCLUDE[net_native](../../../includes/net-native-md.md)] araç zinciri. Yöntem için dinamik meta veri yoksa, şu özel durum ne zaman oluşturulur <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> yöntemi çağrılır:  
  
    ```  
    MakeGenericMethod() cannot create this generic method instantiation because the instantiation was not metadata-enabled: 'App1.Class1.GenMethod<Int32>(Int32)'.  
    ```  
  
 Aşağıdaki çalışma zamanı yönergeleri, tüm gerekli meta veriler kullanılabilir emin olun:  
  
```xml  
<Type Name="App1.Class1" Browse="Required PublicAndInternal">  
   <MethodInstantiation Name="GenMethod" Arguments="System.Int32" Dynamic="Required"/>  
</Type>  
```  
  
 A `MethodInstantiation` yönergesi her farklı dinamik olarak çağrılır yöntemi örnek oluşturma için gereklidir ve `Arguments` öğesi her farklı örneklemesi bağımsız yansıtacak şekilde güncelleştirilir.  
  
## <a name="arraycreateinstance-and-typemaketypearray-methods"></a>Array.CreateInstance ve Type.MakeTypeArray yöntemleri  
 Aşağıdaki örnek çağrıları <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> ve <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> bir türündeki yöntemlere `Class1`.  
  
 [!code-csharp[ProjectN#3](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/array1.cs#3)]  
  
 Dizi meta veri varsa, aşağıdaki hata sonuçları:  
  
```  
This operation cannot be carried out as metadata for the following type was removed for performance reasons:  
  
App1.Class1[]  
  
Unfortunately, no further information is available.  
```  
  
 `Browse` dizi türü için meta verilerini dinamik olarak örneği oluşturmak için gereklidir.  Dinamik örnek oluşturma, şu çalışma zamanı yönerge sağlayan `Class1[]`.  
  
```xml  
<Type Name="App1.Class1[]" Browse="Required Public" />  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Başlarken](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Çalışma Zamanı Yönergeleri (rd.xml) Yapılandırma Dosyası Başvurusu](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)
