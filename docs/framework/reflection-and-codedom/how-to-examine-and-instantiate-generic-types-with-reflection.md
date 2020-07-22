---
title: 'Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma'
description: Bkz. yansıma ile genel türleri İnceleme ve örnek oluşturma. IsGenericType, IsGenericParameter ve GenericParameterPosition özelliklerini kullanın.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
ms.openlocfilehash: b57a0ed0c809da442dc9fcf202ad364060971f80
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865105"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma
Genel türler hakkında bilgi, <xref:System.Type> genel türü temsil eden bir nesneyi inceleyerek, diğer türlerle ilgili bilgilerle aynı şekilde alınır: Prensibi, genel bir türün <xref:System.Type> genel tür parametrelerini temsil eden bir nesne listesi içerir. Bu bölümdeki ilk yordam genel türleri inceler.  
  
 <xref:System.Type>Tür bağımsız değişkenlerini genel tür tanımının tür parametrelerine bağlayarak, oluşturulmuş bir türü temsil eden bir nesne oluşturabilirsiniz. İkinci yordam bunu gösterir.  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>Genel bir tür ve tür parametrelerini incelemek için  
  
1. <xref:System.Type>Genel türü temsil eden bir örneğini alır. Aşağıdaki kodda, türü C# işleci kullanılarak elde edilir `typeof` ( `GetType` Visual Basic `typeid` Visual C++). <xref:System.Type>Nesne almanın diğer yolları için bkz. sınıf konusu <xref:System.Type> . Bu yordamın geri kalanında, türünün adlı bir yöntem parametresinde yer aldığı unutulmamalıdır `t` .  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. <xref:System.Type.IsGenericType%2A>Türün genel olup olmadığını anlamak için özelliğini kullanın ve <xref:System.Type.IsGenericTypeDefinition%2A> türün genel tür tanımı olup olmadığını anlamak için özelliğini kullanın.  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. Yöntemini kullanarak genel tür bağımsız değişkenlerini içeren bir dizi alın <xref:System.Type.GetGenericArguments%2A> .  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. Her tür bağımsız değişkeni için, bir tür parametresi (örneğin, genel tür tanımında) veya tür parametresi için belirtilmiş bir tür (örneğin, oluşturulmuş bir tür için), <xref:System.Type.IsGenericParameter%2A> özelliğini kullanarak.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. Tür sisteminde, genel tür parametresi <xref:System.Type> , normal türler gibi bir örneği tarafından temsil edilir. Aşağıdaki kod, <xref:System.Type> genel bir tür parametresini temsil eden bir nesnenin adını ve parametre konumunu görüntüler. Burada parametre konumu önemsiz bir bilgi; başka bir genel türün tür bağımsız değişkeni olarak kullanılmış bir tür parametresi incelerken daha fazla ilgi çekici olur.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. <xref:System.Type.GetGenericParameterConstraints%2A>Tüm kısıtlamaları tek bir dizide elde etmek için yöntemini kullanarak bir genel tür parametresinin temel tür kısıtlamasını ve arabirim kısıtlamalarını saptayın. Kısıtlamaların belirli bir sırada olması garanti edilmez.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. Bir <xref:System.Type.GenericParameterAttributes%2A> tür parametresindeki özel kısıtlamaları (örneğin, bir başvuru türü olması gerekir) bulmaya yönelik özelliğini kullanın. Özelliği, aşağıdaki kodda gösterildiği gibi, bir varyansı temsil eden değerleri de içerir.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. Özel kısıtlama öznitelikleri bayraklardır ve <xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType> hiçbir özel kısıtlama temsil eden aynı bayrak (), hiçbir Kovaryans veya değişken varyans de temsil eder. Bu nedenle, bu koşullardan biri için test etmek üzere uygun maskeyi kullanmanız gerekir. Bu durumda, <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> özel kısıtlama bayraklarını yalıtmak için kullanın.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>Genel türde bir örnek oluşturma  
 Genel tür bir şablon gibidir. Genel tür parametreleri için gerçek türler belirtmediğiniz müddetçe, bunun örneklerini oluşturamazsınız. Bunu çalışma zamanında, yansıma kullanarak yapmak için <xref:System.Type.MakeGenericType%2A> yöntemi gerekir.  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>Genel türün bir örneğini oluşturmak için  
  
1. <xref:System.Type>Genel türü temsil eden bir nesne alır. Aşağıdaki kod, genel türü <xref:System.Collections.Generic.Dictionary%602> iki farklı şekilde alır: <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> yöntemi tanımlayan bir dize ile yöntem aşırı yüklemesini kullanarak ve <xref:System.Type.GetGenericTypeDefinition%2A> oluşturulan tür üzerinde yöntemini çağırarak `Dictionary\<String, Example>` ( `Dictionary(Of String, Example)` Visual Basic). <xref:System.Type.MakeGenericType%2A>Yöntemi genel bir tür tanımı gerektiriyor.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. Tür parametrelerinin yerine geçecek tür bağımsız değişkenleri dizisi oluşturun. Dizi, <xref:System.Type> tür parametresi listesinde göründükleri şekilde doğru sayıda nesne içermelidir. Bu durumda, anahtar (ilk tür parametresi) türündedir <xref:System.String> ve sözlükteki değerler adlı bir sınıfın örnekleridir `Example` .  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. Tür <xref:System.Type.MakeGenericType%2A> bağımsız değişkenlerini tür parametrelerine bağlamak ve türü oluşturmak için yöntemini çağırın.  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. <xref:System.Activator.CreateInstance%28System.Type%29>Oluşturulmuş türden bir nesne oluşturmak için yöntem aşırı yüklemesini kullanın. Aşağıdaki kod, `Example` elde edilen nesnede sınıfının iki örneğini depolar `Dictionary<String, Example>` .  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, `DisplayGenericType` genel tür tanımlarını ve kodda kullanılan oluşturulmuş türleri incelemek için bir yöntem tanımlar ve bilgilerini görüntüler. `DisplayGenericType`Yöntemi <xref:System.Type.IsGenericType%2A> ,, <xref:System.Type.IsGenericParameter%2A> ve <xref:System.Type.GenericParameterPosition%2A> özelliklerinin ve <xref:System.Type.GetGenericArguments%2A> yönteminin nasıl kullanılacağını gösterir.  
  
 Örnek ayrıca `DisplayGenericParameter` genel tür parametresini İnceleme ve kısıtlamalarını görüntüleme yöntemini tanımlar.  
  
 Kod örneği, tür parametresi kısıtlamalarını gösteren genel bir tür da dahil olmak üzere bir dizi test türü tanımlar ve bu türler hakkındaki bilgilerin nasıl görüntüleneceğini gösterir.  
  
 Örnek, <xref:System.Collections.Generic.Dictionary%602> türünde bağımsız değişkenlerin bir dizisini oluşturarak ve yöntemini çağırarak sınıfından bir tür oluşturur <xref:System.Type.MakeGenericType%2A> . Program, <xref:System.Type> kullanılarak oluşturulan nesneyi <xref:System.Type.MakeGenericType%2A> <xref:System.Type> `typeof` (Visual Basic) kullanarak, aynı olduğunu gösteren ile karşılaştırır `GetType` . Benzer şekilde, program, <xref:System.Type.GetGenericTypeDefinition%2A> oluşturulan türün genel tür tanımını elde etmek için yöntemini kullanır ve <xref:System.Type> sınıfı temsil eden nesneyle karşılaştırır <xref:System.Collections.Generic.Dictionary%602> .  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [Yansıma ve Genel Türler](reflection-and-generic-types.md)
- [Tür Bilgilerini Görüntüleme](viewing-type-information.md)
- [Genel Türler](../../standard/generics/index.md)
