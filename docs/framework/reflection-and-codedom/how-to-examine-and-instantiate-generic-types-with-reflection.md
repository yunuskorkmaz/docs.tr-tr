---
title: 'Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- reflection, generic types
- generics [.NET Framework], reflection
ms.assetid: f93b03b0-1778-43fc-bc6d-35983d210e74
ms.openlocfilehash: 62e4e066740d0422f8f7045b043a5725278c209c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130130"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma
Genel türler hakkında bilgi, genel türü temsil eden bir <xref:System.Type> nesnesini inceleyerek, diğer türlerle ilgili bilgilerle aynı şekilde alınır: Prensibi, genel bir türün genel tür parametrelerini temsil eden <xref:System.Type> nesnelerinin bir listesini içerir. Bu bölümdeki ilk yordam genel türleri inceler.  
  
 Tür bağımsız değişkenlerini genel tür tanımının tür parametrelerine bağlayarak, oluşturulmuş bir türü temsil eden <xref:System.Type> bir nesne oluşturabilirsiniz. İkinci yordam bunu gösterir.  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>Genel bir tür ve tür parametrelerini incelemek için  
  
1. Genel türü temsil eden <xref:System.Type> örneğini alır. Aşağıdaki kodda, türü C# `typeof` işleci (`GetType` Visual Basic, görsel C++'te `typeid`) kullanılarak elde edilir. <xref:System.Type> nesnesini almanın diğer yolları için <xref:System.Type> sınıfı konusuna bakın. Bu yordamın geri kalanında, türün `t`adlı bir yöntem parametresinde yer aldığı unutulmamalıdır.  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. Türün genel olup olmadığını anlamak için <xref:System.Type.IsGenericType%2A> özelliğini kullanın ve türün genel tür tanımı olup olmadığını anlamak için <xref:System.Type.IsGenericTypeDefinition%2A> özelliğini kullanın.  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <xref:System.Type.GetGenericArguments%2A> yöntemini kullanarak genel tür bağımsız değişkenlerini içeren bir dizi alın.  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. Her tür bağımsız değişkeni için, <xref:System.Type.IsGenericParameter%2A> özelliğini kullanarak bir tür parametresi (örneğin, bir genel tür tanımında) veya tür parametresi için belirtilmiş bir tür (örneğin, oluşturulmuş bir tür) olup olmadığını saptayın.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. Tür sisteminde, genel tür parametresi, normal türlerin olduğu gibi bir <xref:System.Type>örneğiyle temsil edilir. Aşağıdaki kod, bir genel tür parametresini temsil eden bir <xref:System.Type> nesnesinin ad ve parametre konumunu görüntüler. Burada parametre konumu önemsiz bir bilgi; başka bir genel türün tür bağımsız değişkeni olarak kullanılmış bir tür parametresi incelerken daha fazla ilgi çekici olur.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. Tüm kısıtlamaları tek bir dizide elde etmek için <xref:System.Type.GetGenericParameterConstraints%2A> yöntemini kullanarak genel tür kısıtlamasının temel tür kısıtlamasını ve arabirim kısıtlamalarını saptayın. Kısıtlamaların belirli bir sırada olması garanti edilmez.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. Bir tür parametresindeki özel kısıtlamaları (örneğin, bir başvuru türü olması gibi) keşfetmesi için <xref:System.Type.GenericParameterAttributes%2A> özelliğini kullanın. Özelliği, aşağıdaki kodda gösterildiği gibi, bir varyansı temsil eden değerleri de içerir.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. Özel kısıtlama öznitelikleri bayraklardır ve hiçbir özel kısıtlama temsil eden aynı bayrak (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>), hiçbir Kovaryans veya değişken varyansı de temsil eder. Bu nedenle, bu koşullardan biri için test etmek üzere uygun maskeyi kullanmanız gerekir. Bu durumda, özel kısıtlama bayraklarını yalıtmak için <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> kullanın.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>Genel türde bir örnek oluşturma  
 Genel tür bir şablon gibidir. Genel tür parametreleri için gerçek türler belirtmediğiniz müddetçe, bunun örneklerini oluşturamazsınız. Bunu çalışma zamanında, yansıma kullanarak yapmak için <xref:System.Type.MakeGenericType%2A> yöntemi gerekir.  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>Genel türün bir örneğini oluşturmak için  
  
1. Genel türü temsil eden bir <xref:System.Type> nesnesi alır. Aşağıdaki kod, genel tür <xref:System.Collections.Generic.Dictionary%602> iki farklı şekilde alır: türü tanımlayan bir dize ile <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini kullanarak ve oluşturulan tür `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` Visual Basic) üzerinde <xref:System.Type.GetGenericTypeDefinition%2A> yöntemini çağırarak. <xref:System.Type.MakeGenericType%2A> yöntemi genel bir tür tanımı gerektiriyor.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. Tür parametrelerinin yerine geçecek tür bağımsız değişkenleri dizisi oluşturun. Dizi, tür parametresi listesinde göründükleri şekilde doğru sayıda <xref:System.Type> nesnesi içermelidir. Bu durumda, anahtar (ilk tür parametresi) <xref:System.String>türündedir ve sözlükteki değerler `Example`adlı bir sınıfın örnekleridir.  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. Tür bağımsız değişkenlerini tür parametrelerine bağlamak ve türü oluşturmak için <xref:System.Type.MakeGenericType%2A> yöntemini çağırın.  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. Oluşturulmuş türden bir nesne oluşturmak için <xref:System.Activator.CreateInstance%28System.Type%29> yöntemi aşırı yüklemesini kullanın. Aşağıdaki kod, sonuçta elde edilen `Dictionary<String, Example>` nesnesinde `Example` sınıfının iki örneğini depolar.  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, genel tür tanımlarını incelemek için bir `DisplayGenericType` yöntemini ve kodda kullanılan oluşturulmuş türleri tanımlar ve bilgilerini görüntüler. `DisplayGenericType` yöntemi <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>ve <xref:System.Type.GenericParameterPosition%2A> özelliklerinin ve <xref:System.Type.GetGenericArguments%2A> yönteminin nasıl kullanılacağını gösterir.  
  
 Örnek ayrıca bir genel tür parametresini incelemek ve kısıtlamalarını göstermek için bir `DisplayGenericParameter` yöntemi tanımlar.  
  
 Kod örneği, tür parametresi kısıtlamalarını gösteren genel bir tür da dahil olmak üzere bir dizi test türü tanımlar ve bu türler hakkındaki bilgilerin nasıl görüntüleneceğini gösterir.  
  
 Örnek, <xref:System.Collections.Generic.Dictionary%602> sınıfından bir tür oluşturur ve <xref:System.Type.MakeGenericType%2A> yöntemini çağırır. Program, <xref:System.Type.MakeGenericType%2A> kullanılarak oluşturulan <xref:System.Type> nesnesini, aynı olduğunu gösteren `typeof` (`GetType`) ile elde edilen <xref:System.Type> nesnesiyle karşılaştırır. Benzer şekilde, program, oluşturulan türün genel tür tanımını elde etmek için <xref:System.Type.GetGenericTypeDefinition%2A> yöntemini kullanır ve onu <xref:System.Collections.Generic.Dictionary%602> sınıfını temsil eden <xref:System.Type> nesnesiyle karşılaştırır.  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [Yansıma ve Genel Türler](reflection-and-generic-types.md)
- [Tür Bilgilerini Görüntüleme](viewing-type-information.md)
- [Genel Türler](../../standard/generics/index.md)
