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
ms.openlocfilehash: b0f964ac73f070b99cdfd06e9037d06ce7888938
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397578"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma
Genel türler hakkında bilgi tıpkı diğer türleri hakkında bilgi elde edilir: inceleniyor tarafından bir <xref:System.Type> genel türünü temsil eden nesne. İlkeye genel bir tür listesini içeren farktır <xref:System.Type> genel tür parametreleri temsil eden nesne. Bu bölümdeki ilk yordam genel türler inceler.  
  
 Oluşturabileceğiniz bir <xref:System.Type> genel tür tanımında türü parametreleri bağlama tür bağımsız değişkeni tarafından oluşturulan bir türü temsil eden nesne. İkinci yordam bu gösterir.  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>Genel bir tür ve tür parametrelerinin incelemek için  
  
1.  Bir örneğini almak <xref:System.Type> , genel türünü temsil eder. Aşağıdaki kodda, C# kullanarak türü elde `typeof` işleci (`GetType` Visual Basic'te `typeid` Visual C++'ta). Bkz: <xref:System.Type> almak diğer yolları için sınıf konusuna bir <xref:System.Type> nesnesi. Bu yordamın geri kalanını içinde adlandırılmış bir yöntem parametresinde türü içeriyordu Not `t`.  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2.  Kullanmak <xref:System.Type.IsGenericType%2A> türü genel olup olmadığını belirlemek ve kullanmak için özelliği <xref:System.Type.IsGenericTypeDefinition%2A> özellik türü bir genel tür tanımı olup olmadığını belirlemek için.  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3.  Kullanarak genel tür bağımsız değişkenleri içeren bir dizi almak <xref:System.Type.GetGenericArguments%2A> yöntemi.  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4.  Her tür bağımsız değişkeni için bir tür parametresi (örneğin, bir genel tür tanımında) veya (örneğin, gelen bir oluşturulan türü), bir tür parametresi için belirtilen bir tür olup olmadığını belirleme kullanarak <xref:System.Type.IsGenericParameter%2A> özelliği.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5.  Tür sistemi genel tür parametresi bir örneği tarafından temsil edilen <xref:System.Type>, normal türleri gibi. Aşağıdaki kod adı ve parametre konumunu görüntüler bir <xref:System.Type> genel tür parametresi temsil eden nesne. Buraya Önemsiz bilgileri parametresi konumdur; Bunu başka bir genel tür bir tür bağımsız değişkeni olarak kullanılan bir tür parametresi incelerken daha fazla ilgilendirir.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6.  Temel tür sınırlaması ve bir genel tür parametresi arabirimi kısıtlamaları kullanarak belirlemek <xref:System.Type.GetGenericParameterConstraints%2A> tek bir dizi tüm kısıtlamalar elde etmek için yöntemi. Kısıtlamaları belirli bir sırada olması garanti edilmez.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7.  Kullanım <xref:System.Type.GenericParameterAttributes%2A> özelliği bir başvuru türü olmasını gerektiren gibi bir tür parametresi özel kısıtlamalar keşfedin. Özellik ayrıca aşağıdaki kodda gösterildiği gibi devre dışı maskeleyebilirsiniz farkı temsil eden değerlerini içerir.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8.  Bayrakları ve aynı bayrağı özel kısıtlaması öznitelikleridir (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) özel temsil eden kısıtlamaları da temsil eden Kovaryans veya değişken karşıtı yok. Bu nedenle, ya da bu koşullar test etmek için uygun maskesi kullanmanız gerekir. Bu durumda, kullanarak <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> özel kısıtlaması bayrakları yalıtmak için.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>Genel bir tür örneği oluşturma  
 Genel bir tür gibi bir şablondur. Genel tür parametreleri gerçek türlerinde belirtmediğiniz sürece örneği oluşturulamıyor. Yansıma, kullanarak çalışma zamanında bunun için gerektirir <xref:System.Type.MakeGenericType%2A> yöntemi.  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>Genel bir tür örneği oluşturmak için  
  
1.  Alma bir <xref:System.Type> genel türünü temsil eden nesne. Genel türü aşağıdaki kodu alır <xref:System.Collections.Generic.Dictionary%602> iki farklı yolla: kullanarak <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini türünü tanımlayan bir dize ile çağırarak <xref:System.Type.GetGenericTypeDefinition%2A> oluşturulan türünün yöntemi `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` içinde Visual Basic). <xref:System.Type.MakeGenericType%2A> Yöntemi, bir genel tür tanımı gerektirir.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2.  Tür bağımsız değişkeni için tür parametreleri değiştirmek için bir dizi oluşturun. Dizi doğru sayıda içermelidir <xref:System.Type> türü parametre listesinde göründükleri gibi aynı sırada nesneleri. Bu durumda, anahtarı (ilk tür parametresi) türüdür <xref:System.String>, ve sözlükteki değerleri adlı bir sınıfın örneklerini `Example`.  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3.  Çağrı <xref:System.Type.MakeGenericType%2A> tür bağımsız değişkeni tür parametreleri bağlamak ve türü oluşturmak için yöntem.  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4.  Kullanım <xref:System.Activator.CreateInstance%28System.Type%29> oluşturulan türünde bir nesne oluşturmak için yöntemi aşırı yüklemesini. Aşağıdaki kod iki örneğini depolar `Example` elde edilen içinde sınıf `Dictionary<String, Example>` nesnesi.  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde tanımlayan bir `DisplayGenericType` genel tür tanımları ve kod içinde kullanılan oluşturulan türler inceleyin ve kendi bilgilerini görüntülemek için yöntem. `DisplayGenericType` Yönteminin nasıl kullanılacağını gösterir <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, ve <xref:System.Type.GenericParameterPosition%2A> özellikleri ve <xref:System.Type.GetGenericArguments%2A> yöntemi.  
  
 Örnek ayrıca tanımlar bir `DisplayGenericParameter` genel tür parametresi inceleyin ve kendi kısıtlamaları görüntülemek için yöntem.  
  
 Kod örneği, bir dizi türü parametresi kısıtlamaları gösterir ve bu tür hakkındaki bilgileri görüntülemek nasıl gösterir genel bir tür dahil olmak üzere test türü tanımlar.  
  
 Örnek bir türden yapıları <xref:System.Collections.Generic.Dictionary%602> tür bağımsız değişkenleri dizisini oluşturarak ve çağırma sınıfı <xref:System.Type.MakeGenericType%2A> yöntemi. Program karşılaştırır <xref:System.Type> kullanılarak oluşturulan nesne <xref:System.Type.MakeGenericType%2A> ile bir <xref:System.Type> kullanarak elde nesne `typeof` (`GetType` Visual Basic'te), bunların aynı olduğunu gösteren. Benzer şekilde, programın kullandığı <xref:System.Type.GetGenericTypeDefinition%2A> oluşturulan türün genel tür tanımında elde etmek için yöntemi ve kendisine karşılaştırır <xref:System.Type> nesnesini temsil eden <xref:System.Collections.Generic.Dictionary%602> sınıfı.  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   C# kodunu `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.  
  
-   Hiçbir ek derleme başvurularını gereklidir.  
  
-   Csc.exe, vbc.exe veya cl.exe kullanarak komut satırında kodu derleyin. Visual Studio'da Kodu derlemek için bir konsol uygulama projesi şablonunda yerleştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Type>  
 <xref:System.Reflection.MethodInfo>  
 [Yansıma ve Genel Türler](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)  
 [Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)  
 [Genel Türler](../../../docs/standard/generics/index.md)
