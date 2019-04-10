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
ms.openlocfilehash: ddddc746eb29c526adb8a15fc6ac40acc22954cf
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337233"
---
# <a name="how-to-examine-and-instantiate-generic-types-with-reflection"></a>Nasıl yapılır: Yansıma ile Genel Türleri İnceleme ve Örnek Oluşturma
Genel türler hakkında bilgi tıpkı diğer türler hakkında bilgi elde edilir: inceleme tarafından bir <xref:System.Type> genel türü temsil eden nesne. İlkeye genel bir türün bir listesi olduğunu fark <xref:System.Type> , genel tür parametrelerini temsil eden nesneleri. Bu bölümdeki ilk yordam, genel türler inceler.  
  
 Oluşturabileceğiniz bir <xref:System.Type> oluşturulan tür, genel tür tanımı için tür parametreleri bağlama tür bağımsız değişkeni tarafından temsil eden nesne. İkinci yordam bu gösterir.  
  
### <a name="to-examine-a-generic-type-and-its-type-parameters"></a>Genel bir tür ve tür parametrelerinden biri incelemek için  
  
1. Bir kopyasını almak <xref:System.Type> , genel türü temsil eder. Aşağıdaki kodda, türü kullanılarak edinilen C# `typeof` işleci (`GetType` Visual Basic'te `typeid` Visual C++'ta). Bkz: <xref:System.Type> almanın diğer yolları için sınıf konusuna bir <xref:System.Type> nesne. Bu yordamın kalan adlı bir yöntem parametre türü içerdiği Not `t`.  
  
     [!code-cpp[HowToGeneric#2](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#2)]
     [!code-csharp[HowToGeneric#2](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#2)]
     [!code-vb[HowToGeneric#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#2)]  
  
2. Kullanma <xref:System.Type.IsGenericType%2A> türünün genel olup olmadığını belirlemek ve özellik <xref:System.Type.IsGenericTypeDefinition%2A> özellik türü bir genel tür tanımı olup olmadığını belirlemek için.  
  
     [!code-cpp[HowToGeneric#3](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#3)]
     [!code-csharp[HowToGeneric#3](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#3)]
     [!code-vb[HowToGeneric#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#3)]  
  
3. Kullanarak genel tür bağımsız değişkenleri içeren bir dizi alma <xref:System.Type.GetGenericArguments%2A> yöntemi.  
  
     [!code-cpp[HowToGeneric#4](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#4)]
     [!code-csharp[HowToGeneric#4](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#4)]
     [!code-vb[HowToGeneric#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#4)]  
  
4. Her tür bağımsız değişkeni için bir tür parametresi (örneğin, bir genel tür tanımında) veya (örneğin, bir oluşturulmuş tür içinde), bir tür parametresi için belirtilen bir tür olup olmadığını belirlemek kullanarak <xref:System.Type.IsGenericParameter%2A> özelliği.  
  
     [!code-cpp[HowToGeneric#5](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#5)]
     [!code-csharp[HowToGeneric#5](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#5)]
     [!code-vb[HowToGeneric#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#5)]  
  
5. İçindeki tür sisteminde, genel tür parametresi bir örneği tarafından temsil edilen <xref:System.Type>sıradan türleri aynı şekilde. Aşağıdaki kod adı ve parametre konumunu görüntüleyen bir <xref:System.Type> bir genel tür parametresini temsil eden nesne. Parametresi, burada Önemsiz bilgi konumudur; Bu, başka bir genel türün tür bağımsız değişkeni kullanılan bir tür parametresi incelerken daha fazla ilgi olur.  
  
     [!code-cpp[HowToGeneric#6](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#6)]
     [!code-csharp[HowToGeneric#6](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#6)]
     [!code-vb[HowToGeneric#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#6)]  
  
6. Temel tür kısıtlaması ve genel tür parametresi kısıtlamaları arabirimi kullanarak belirlemek <xref:System.Type.GetGenericParameterConstraints%2A> tüm kısıtlamalar tek bir dizi elde etmek için yöntemi. Kısıtlamaları herhangi belirli bir sırada olması garanti edilmez.  
  
     [!code-cpp[HowToGeneric#7](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#7)]
     [!code-csharp[HowToGeneric#7](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#7)]
     [!code-vb[HowToGeneric#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#7)]  
  
7. Kullanım <xref:System.Type.GenericParameterAttributes%2A> özelliği özel bir başvuru türü olmasını gerektirme gibi bir tür parametresi kısıtlamaları bulunacak. Özelliği, ayrıca, aşağıdaki kodda gösterildiği gibi devre dışı maskeleyebilirsiniz varyansı gösteren değerleri içerir.  
  
     [!code-cpp[HowToGeneric#8](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#8)]
     [!code-csharp[HowToGeneric#8](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#8)]
     [!code-vb[HowToGeneric#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#8)]  
  
8. Bayraklar ve aynı bayrağı özel kısıtlaması öznitelikleridir (<xref:System.Reflection.GenericParameterAttributes.None?displayProperty=nameWithType>) temsil eden özel kısıtlamaları da temsil Kovaryans veya kontravaryans yok. Bu nedenle, Bu koşullardan birini test etmek için uygun maskesi kullanmanız gerekir. Bu durumda, <xref:System.Reflection.GenericParameterAttributes.SpecialConstraintMask?displayProperty=nameWithType> özel kısıtlaması bayrakları yalıtmak için.  
  
     [!code-cpp[HowToGeneric#9](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#9)]
     [!code-csharp[HowToGeneric#9](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#9)]
     [!code-vb[HowToGeneric#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#9)]  
  
## <a name="constructing-an-instance-of-a-generic-type"></a>Genel bir türün bir örneği oluşturma  
 Genel bir tür gibi bir şablondur. Kendi genel tür parametreleri için gerçek türler belirtmediğiniz sürece örneği oluşturulamıyor. Çalışma zamanında Bunu yapmak için yansıma kullanarak gerektirir <xref:System.Type.MakeGenericType%2A> yöntemi.  
  
#### <a name="to-construct-an-instance-of-a-generic-type"></a>Genel bir türün bir örneğini oluşturmak için  
  
1. Alma bir <xref:System.Type> genel türü temsil eden nesne. Aşağıdaki kod genel tür alır <xref:System.Collections.Generic.Dictionary%602> iki farklı yolla: kullanarak <xref:System.Type.GetType%28System.String%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini çağırarak ve türünü tanımlayan bir dize <xref:System.Type.GetGenericTypeDefinition%2A> oluşturulan tür metodunda `Dictionary\<String, Example>` (`Dictionary(Of String, Example)` içinde Visual Basic). <xref:System.Type.MakeGenericType%2A> Yöntem genel tür tanımı gerektirir.  
  
     [!code-cpp[HowToGeneric#10](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#10)]
     [!code-csharp[HowToGeneric#10](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#10)]
     [!code-vb[HowToGeneric#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#10)]  
  
2. Tür parametreleri için eklenecek tür bağımsız değişkeni bir dizi oluşturun. Dizi doğru sayıda içermelidir <xref:System.Type> türü parametre listesinde göründükleri gibi aynı sırada nesneleri. Bu durumda, anahtar türüdür (ilk tür parametresi) <xref:System.String>, ve sözlükteki değerlerin adlı bir sınıfın örneklerini `Example`.  
  
     [!code-cpp[HowToGeneric#11](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#11)]
     [!code-csharp[HowToGeneric#11](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#11)]
     [!code-vb[HowToGeneric#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#11)]  
  
3. Çağrı <xref:System.Type.MakeGenericType%2A> tür bağımsız değişkenleri için tür parametreleri bağlama ve tür oluşturmak için yöntem.  
  
     [!code-cpp[HowToGeneric#12](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#12)]
     [!code-csharp[HowToGeneric#12](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#12)]
     [!code-vb[HowToGeneric#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#12)]  
  
4. Kullanım <xref:System.Activator.CreateInstance%28System.Type%29> yöntemi aşırı yüklemesi, oluşturulan türde bir nesne oluşturmak için. Aşağıdaki kod iki örneğini depolar `Example` sonuç sınıfı `Dictionary<String, Example>` nesne.  
  
     [!code-cpp[HowToGeneric#13](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#13)]
     [!code-csharp[HowToGeneric#13](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#13)]
     [!code-vb[HowToGeneric#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#13)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği tanımlayan bir `DisplayGenericType` genel tür tanımları ve kod içinde kullanılan oluşturulan türler inceleyin ve kullanıcıların bilgilerini görüntülemek için yöntemi. `DisplayGenericType` Yönteminin nasıl kullanılacağını göstermektedir <xref:System.Type.IsGenericType%2A>, <xref:System.Type.IsGenericParameter%2A>, ve <xref:System.Type.GenericParameterPosition%2A> özellikleri ve <xref:System.Type.GetGenericArguments%2A> yöntemi.  
  
 Örnek ayrıca tanımlar bir `DisplayGenericParameter` genel tür parametresi inceleyin ve kısıtlamaları görüntülemek için yöntemi.  
  
 Kod örneği, tür parametresi kısıtlamaları gösterir ve bu türleri hakkında bilgileri görüntülemeyi gösterir genel bir tür gibi test türleri kümesi tanımlar.  
  
 Bir türden örneğin yapıları <xref:System.Collections.Generic.Dictionary%602> sınıf türü bağımsız değişken bir dizi oluşturarak ve çağırma <xref:System.Type.MakeGenericType%2A> yöntemi. Program karşılaştırır <xref:System.Type> kullanılarak oluşturulan nesne <xref:System.Type.MakeGenericType%2A> ile bir <xref:System.Type> kullanılarak elde edilen nesnenin `typeof` (`GetType` Visual Basic'te), bunların aynı olduğunu gösteren. Benzer şekilde, programın kullandığı <xref:System.Type.GetGenericTypeDefinition%2A> oluşturulan tür, genel tür tanımını almak için yöntemi ve kendisine karşılaştırır <xref:System.Type> nesnesini temsil eden <xref:System.Collections.Generic.Dictionary%602> sınıfı.  
  
 [!code-cpp[HowToGeneric#1](../../../samples/snippets/cpp/VS_Snippets_CLR/HowToGeneric/cpp/ur.cpp#1)]
 [!code-csharp[HowToGeneric#1](../../../samples/snippets/csharp/VS_Snippets_CLR/HowToGeneric/CS/ur.cs#1)]
 [!code-vb[HowToGeneric#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/HowToGeneric/VB/ur.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   C# kodu içeren `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.  
  
-   Hiçbir ek derleme başvurularını gereklidir.  
  
-   Csc.exe, vbc.exe veya cl.exe kullanarak komut satırındaki kodu derleyin. Visual Studio'da Kodu derlemek için bir konsol uygulaması projesi şablonu içine koyun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Type>
- <xref:System.Reflection.MethodInfo>
- [Yansıma ve Genel Türler](../../../docs/framework/reflection-and-codedom/reflection-and-generic-types.md)
- [Tür Bilgilerini Görüntüleme](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)
- [Genel Türler](../../../docs/standard/generics/index.md)
