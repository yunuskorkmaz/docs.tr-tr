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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d6517edcc2784b7d70c08c4d15d837fc1f209c49
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928236"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma
Genel türler hakkında bilgi, genel türü temsil eden bir <xref:System.Type> nesneyi inceleyerek, diğer türlerle ilgili bilgilerle aynı şekilde alınır: Prensibi, genel bir türün genel tür parametrelerini temsil eden bir <xref:System.Type> nesne listesi içerir. Bu bölümdeki ilk yordam genel türleri inceler.  
  
 Tür bağımsız değişkenlerini genel <xref:System.Type> tür tanımının tür parametrelerine bağlayarak, oluşturulmuş bir türü temsil eden bir nesne oluşturabilirsiniz. İkinci yordam bunu gösterir.  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>Genel bir tür ve tür parametrelerini incelemek için  
  
1. Genel türü temsil <xref:System.Type> eden bir örneğini alır. C# `typeof` Aşağıdaki kodda, türü işleci kullanılarak elde edilir (`GetType` Visual Basic, `typeid` görselde C++). Nesne almanın diğer yolları için bkz. sınıfkonusu.<xref:System.Type> <xref:System.Type> Bu yordamın geri kalanında, türünün adlı `t`bir yöntem parametresinde yer aldığı unutulmamalıdır.  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. Türün genel olup olmadığını anlamak için <xref:System.Type.IsGenericTypeDefinition%2A> özelliğinikullanınvetürüngeneltürtanımıolupolmadığınıanlamakiçinözelliğinikullanın.<xref:System.Type.IsGenericType%2A>  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. <xref:System.Type.GetGenericArguments%2A> Yöntemini kullanarak genel tür bağımsız değişkenlerini içeren bir dizi alın.  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. Her tür bağımsız değişkeni için, bir tür parametresi (örneğin, genel tür tanımında) veya tür parametresi için belirtilmiş bir tür (örneğin, oluşturulmuş bir tür için), <xref:System.Type.IsGenericParameter%2A> özelliğini kullanarak.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. Tür sisteminde, genel tür parametresi <xref:System.Type>, normal türler gibi bir örneği tarafından temsil edilir. Aşağıdaki kod, genel bir tür parametresini temsil eden bir <xref:System.Type> nesnenin adını ve parametre konumunu görüntüler. Burada parametre konumu önemsiz bir bilgi; başka bir genel türün tür bağımsız değişkeni olarak kullanılmış bir tür parametresi incelerken daha fazla ilgi çekici olur.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. Tüm kısıtlamaları tek bir dizide elde etmek için <xref:System.Type.GetGenericParameterConstraints%2A> yöntemini kullanarak bir genel tür parametresinin temel tür kısıtlamasını ve arabirim kısıtlamalarını saptayın. Kısıtlamaların belirli bir sırada olması garanti edilmez.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. Bir tür parametresindeki özel kısıtlamaları (örneğin, bir başvuru türü olması gerekir) bulmaya yönelik özelliğinikullanın.<xref:System.Type.GenericParameterAttributes%2A> Özelliği, aşağıdaki kodda gösterildiği gibi, bir varyansı temsil eden değerleri de içerir.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. Özel kısıtlama öznitelikleri bayraklardır ve hiçbir özel kısıtlama temsil eden aynı<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>bayrak (), hiçbir Kovaryans veya değişken varyans de temsil eder. Bu nedenle, bu koşullardan biri için test etmek üzere uygun maskeyi kullanmanız gerekir. Bu durumda, özel kısıtlama <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> bayraklarını yalıtmak için kullanın.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>Genel türde bir örnek oluşturma  
 Genel tür bir şablon gibidir. Genel tür parametreleri için gerçek türler belirtmediğiniz müddetçe, bunun örneklerini oluşturamazsınız. Bunu çalışma zamanında, yansıma kullanarak yapmak için <xref:System.Type.MakeGenericType%2A> yöntemi gerekir.  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>Genel türün bir örneğini oluşturmak için  
  
1. Genel türü <xref:System.Type> temsil eden bir nesne alır. Aşağıdaki <xref:System.Collections.Generic.Dictionary%602> kod, genel türü iki farklı şekilde alır: <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> yöntemi tanımlayan bir dize ile yöntem aşırı yüklemesini kullanarak ve oluşturulan tür `Dictionary\<String, Example>` üzerinde <xref:System.Type.GetGenericTypeDefinition%2A> yöntemini çağırarak (`Dictionary(Of String, Example)` Visual Basic). <xref:System.Type.MakeGenericType%2A> Yöntemi genel bir tür tanımı gerektiriyor.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. Tür parametrelerinin yerine geçecek tür bağımsız değişkenleri dizisi oluşturun. Dizi, tür parametresi listesinde göründükleri şekilde doğru <xref:System.Type> sayıda nesne içermelidir. Bu durumda, anahtar (ilk tür parametresi) türündedir <xref:System.String>ve sözlükteki değerler adlı `Example`bir sınıfın örnekleridir.  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. Tür bağımsız değişkenlerini tür parametrelerine bağlamak ve türü oluşturmak için yönteminiçağırın.<xref:System.Type.MakeGenericType%2A>  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. Oluşturulmuş türden bir nesne oluşturmak için yöntemaşırıyüklemesinikullanın.<xref:System.Activator.CreateInstance%28System.Type%29> Aşağıdaki kod, elde edilen `Example` `Dictionary<String, Example>` nesnede sınıfının iki örneğini depolar.  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, genel tür `DisplayGenericType` tanımlarını ve kodda kullanılan oluşturulmuş türleri incelemek için bir yöntem tanımlar ve bilgilerini görüntüler. Yöntemi,<xref:System.Type.IsGenericType%2A> ,ve<xref:System.Type.GenericParameterPosition%2A> özelliklerinin ve<xref:System.Type.GetGenericArguments%2A> yönteminin nasıl kullanılacağını gösterir. <xref:System.Type.IsGenericParameter%2A> `DisplayGenericType`  
  
 Örnek ayrıca genel tür parametresini `DisplayGenericParameter` İnceleme ve kısıtlamalarını görüntüleme yöntemini tanımlar.  
  
 Kod örneği, tür parametresi kısıtlamalarını gösteren genel bir tür da dahil olmak üzere bir dizi test türü tanımlar ve bu türler hakkındaki bilgilerin nasıl görüntüleneceğini gösterir.  
  
 Örnek, türünde bağımsız değişkenlerin bir dizisini <xref:System.Collections.Generic.Dictionary%602> oluşturarak ve <xref:System.Type.MakeGenericType%2A> yöntemini çağırarak sınıfından bir tür oluşturur. Program, kullanılarak <xref:System.Type.MakeGenericType%2A> oluşturulan <xref:System.Type> nesneyi ( `typeof` <xref:System.Type> VisualBasic)kullanarak,aynıolduğunugösterenilekarşılaştırır.`GetType` Benzer şekilde, program, oluşturulan <xref:System.Type.GetGenericTypeDefinition%2A> türün genel tür tanımını elde etmek için yöntemini kullanır ve <xref:System.Collections.Generic.Dictionary%602> sınıfı temsil eden <xref:System.Type> nesneyle karşılaştırır.  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [Yansıma ve Genel Türler](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
- [Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Genel Türler](../../standard/generics/index.md)
