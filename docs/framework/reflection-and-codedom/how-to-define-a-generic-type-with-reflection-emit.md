---
title: 'Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- generics [.NET Framework], dynamic types
- reflection emit, generic types
ms.assetid: 07d5f01a-7b5b-40ea-9b15-f21561098fe4
ms.openlocfilehash: b553fd2235c73cf879474dc4f44f958dddcb649c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130165"
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a>Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama
Bu konu, iki tür parametresiyle basit genel bir tür oluşturmayı, sınıf kısıtlamalarını, arabirim kısıtlamalarını ve özel kısıtlamaları tür parametrelerine uygulamayı ve sınıfın tür parametrelerini parametre türleri olarak kullanan üyelerin nasıl oluşturulacağını gösterir ve dönüş türleri.  
  
> [!IMPORTANT]
> Yalnızca genel bir türe ait olduğundan ve bu türün tür parametrelerini kullandığından bir yöntem genel değildir. Bir yöntem, yalnızca kendi tür parametresi listesine sahipse geneldir. Bu örnekte olduğu gibi genel türlerde yöntemlerin çoğu genel değildir. Genel bir yöntem yaymayla ilgili bir örnek için bkz. [nasıl yapılır: yansıma yayma Ile genel yöntem tanımlama](how-to-define-a-generic-method-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-type"></a>Genel bir tür tanımlamak için  
  
1. `GenericEmitExample1`adlı bir dinamik derleme tanımlayın. Bu örnekte, derleme yürütülür ve diske kaydedilir, bu nedenle <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> belirtilir.  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2. Dinamik bir modül tanımlayın. Bir derleme yürütülebilir modüllerden oluşur. Tek modüllü bir derlemede modül adı derleme adıyla aynıdır ve dosya adı modül adı artı bir uzantıdır.  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3. Bir sınıf tanımlayın. Bu örnekte, sınıfı `Sample`olarak adlandırılır.  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4. Parametrelerinin adlarını içeren bir dize dizisini <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> yöntemine geçirerek `Sample` genel tür parametrelerini tanımlayın. Bu, sınıfı genel bir tür yapar. Dönüş değeri, oluşturulan kodunuzda kullanılabilen tür parametrelerini temsil eden <xref:System.Reflection.Emit.GenericTypeParameterBuilder> nesnelerden oluşan bir dizidir.  
  
     Aşağıdaki kodda, `Sample` tür parametreleri `TFirst` ve `TSecond`olan genel bir tür haline gelir. Kodu daha kolay okunabilir hale getirmek için her <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, tür parametresiyle aynı ada sahip bir değişkene yerleştirilir.  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5. Tür parametrelerine özel kısıtlamalar ekleyin. Bu örnekte, `TFirst` parametresi parametresiz oluşturucular olan türler ve başvuru türleri için kısıtlanmıştır.  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6. İsteğe bağlı olarak tür parametrelerine sınıf ve arabirim kısıtlamaları ekleyin. Bu örnekte, `TFirst` parametresi, değişken `baseType`bulunan <xref:System.Type> nesne tarafından temsil edilen temel sınıftan türetilmiş türler için kısıtlanmıştır ve türleri değişkenlerde bulunan arabirimleri uygular `interfaceA` ve @no __t_4_ . Bu değişkenlerin bildirimi ve atanması için kod örneğine bakın.  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7. Bir alan tanımlayın. Bu örnekte, alanın türü tür parametresiyle belirtilir `TFirst`. <xref:System.Reflection.Emit.GenericTypeParameterBuilder> <xref:System.Type>türetilir, böylece bir tür kullanılabilir her yerde genel tür parametrelerini kullanabilirsiniz.  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8. Genel türün tür parametrelerini kullanan bir yöntem tanımlayın. Bu tür yöntemlerin, kendi tür parametre listelerine sahip olmadıkları müddetçe genel olmadığına unutmayın. Aşağıdaki kod, bir `TFirst` dizisi alan ve dizinin tüm öğelerini içeren bir `List<TFirst>` (`List(Of TFirst)`) döndüren bir `static` yöntemi (Visual Basic`Shared`) tanımlar. Bu yöntemi tanımlamak için, <xref:System.Type.MakeGenericType%2A> genel tür tanımına `List<T>`çağırarak tür `List<TFirst>` oluşturulması gerekir. (`T`, genel tür tanımını almak için `typeof` işlecini (Visual Basic içinde`GetType`) kullandığınızda atlanır.) Parametre türü <xref:System.Type.MakeArrayType%2A> yöntemi kullanılarak oluşturulur.  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. Yöntem gövdesini yay. Yöntem gövdesi, giriş dizisini yığına yükleyen üç opbebeden oluşur, `IEnumerable<TFirst>` (giriş öğelerini listeye yerleştirme tüm işleri yapar) `List<TFirst>` oluşturucusunu çağırır ve (yığında yeni <xref:System.Collections.Generic.List%601> nesnesini bırakır). Bu kodu yayın zor kısmı oluşturucuyu alıyor.  
  
     <xref:System.Type.GetConstructor%2A> yöntemi <xref:System.Reflection.Emit.GenericTypeParameterBuilder>desteklenmez, bu nedenle `List<TFirst>` oluşturucusunu doğrudan almak mümkün değildir. İlk olarak, genel tür tanımı `List<T>` oluşturucusunu almak ve sonra karşılık gelen `List<TFirst>`oluşturucusuna dönüştüren bir yöntemi çağırmak gereklidir.  
  
     Bu kod örneği için kullanılan Oluşturucu bir `IEnumerable<T>`alır. Bununla birlikte, bunun <xref:System.Collections.Generic.IEnumerable%601> genel arabiriminin genel tür tanımı olmadığına unutmayın; Bunun yerine, `List<T>` tür `T` parametresi `IEnumerable<T>``T` tür parametresi için yerine kullanılmalıdır. (Bu, her iki tür de `T`adlı tür parametrelerine sahip olduğundan kafa karıştırıcı görünmektedir. Bu nedenle, bu kod örneği `TFirst` ve `TSecond`adlarını kullanır.) Oluşturucu bağımsız değişkeninin türünü almak için, genel tür tanımı `IEnumerable<T>` başlatın ve `List<T>`ilk genel tür parametresiyle <xref:System.Type.MakeGenericType%2A> çağırın. Oluşturucu bağımsız değişken listesi, bu durumda yalnızca bir bağımsız değişken ile bir dizi olarak geçirilmelidir.  
  
    > [!NOTE]
    > Genel tür tanımı, içinde C#`typeof` işlecini kullandığınızda veya Visual Basic `GetType` işlecini kullandığınızda `IEnumerable(Of )` `IEnumerable<>` olarak ifade edilir.  
  
     Artık, genel tür tanımında <xref:System.Type.GetConstructor%2A> çağırarak `List<T>` oluşturucusunu almak mümkündür. Bu oluşturucuyu karşılık gelen `List<TFirst>`oluşturucusuna dönüştürmek için, `List<T>` `List<TFirst>` ve oluşturucuyu statik <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> metoduna geçirin.  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. Türü oluşturun ve dosyayı kaydedin.  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. Yöntemi çağırın. `ExampleMethod` genel değildir ancak ait olduğu tür geneldir, bu nedenle çağrılabilecek bir <xref:System.Reflection.MethodInfo> almak için `Sample`tür tanımından oluşturulmuş bir tür oluşturmanız gerekir. Oluşturulan tür, bir başvuru türü olduğundan ve varsayılan parametresiz oluşturucusu ve `TSecond`kısıtlamalarını karşılayan `ExampleDerived` sınıfı olduğundan, `TFirst` kısıtlamalarını karşılayan `Example` sınıfını kullanır. (`ExampleDerived` kodu örnek kod bölümünde bulunabilir.) Bu iki tür, oluşturulan türü oluşturmak için <xref:System.Type.MakeGenericType%2A> geçirilir. <xref:System.Reflection.MethodInfo> daha sonra <xref:System.Type.GetMethod%2A> yöntemi kullanılarak elde edilir.  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. Aşağıdaki kod `Example` nesnelerinin bir dizisini oluşturur, bu diziyi, çağrılacak yöntemin bağımsız değişkenlerini temsil eden <xref:System.Object> türünde bir diziye koyar ve bunları <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> yöntemine geçirir. Yöntem `static`olduğundan <xref:System.Reflection.MethodBase.Invoke%2A> yönteminin ilk bağımsız değişkeni null bir başvurudur.  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir temel sınıf ve iki arabirim ile birlikte `Sample`adlı bir sınıfı tanımlar. Program `Sample`için iki genel tür parametresi tanımlar ve genel bir türe dönüştürür. Tür parametreleri, bir türü genel yapan tek şeydir. Program, tür parametrelerinin tanımından önce ve sonra bir test iletisi görüntüleyerek bunu gösterir.  
  
 Tür parametresi `TSecond`, temel sınıf ve arabirimleri kullanarak sınıf ve arabirim kısıtlamalarını göstermek için kullanılır ve `TFirst` tür parametresi özel kısıtlamaları göstermek için kullanılır.  
  
 Kod örneği, alan türü için sınıfın tür parametrelerini ve yönteminin parametre ve dönüş türünü kullanarak bir alanı ve yöntemi tanımlar.  
  
 `Sample` sınıfı oluşturulduktan sonra yöntem çağrılır.  
  
 Program, bir genel tür hakkındaki bilgileri ve bir tür parametresindeki özel kısıtlamaları listeleyen bir yöntemi içerir. Bu yöntemler, tamamlanmış `Sample` sınıfıyla ilgili bilgileri göstermek için kullanılır.  
  
 Program, tamamlanmış modülü diske `GenericEmitExample1.dll`olarak kaydeder, böylece [ıldadsm. exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) ile açabilir ve `Sample` sınıfı için MSIL 'yi inceleyebilirsiniz.  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Emit.GenericTypeParameterBuilder>
- [Yansıma yayma kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))
- [Yansıma yayma dinamik derleme senaryoları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tt9483fk(v=vs.100))
