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
Bu konu, iki tür parametresiyle basit genel bir tür oluşturmayı, sınıf kısıtlamalarını, arabirim kısıtlamalarını ve özel kısıtlamaları tür parametrelerine uygulamayı ve sınıfın tür parametrelerini parametre türleri ve dönüş türleri olarak kullanan üyelerin nasıl oluşturulacağını gösterir.  
  
> [!IMPORTANT]
> Yalnızca genel bir türe ait olduğundan ve bu türün tür parametrelerini kullandığından bir yöntem genel değildir. Bir yöntem, yalnızca kendi tür parametresi listesine sahipse geneldir. Bu örnekte olduğu gibi genel türlerde yöntemlerin çoğu genel değildir. Genel bir yöntem yaymayla ilgili bir örnek için bkz. [nasıl yapılır: yansıma yayma Ile genel yöntem tanımlama](how-to-define-a-generic-method-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-type"></a>Genel bir tür tanımlamak için  
  
1. Adlı `GenericEmitExample1`bir dinamik derleme tanımlayın. Bu örnekte, derleme yürütülür ve diske kaydedilir, bu nedenle <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> belirtilir.  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2. Dinamik bir modül tanımlayın. Bir derleme yürütülebilir modüllerden oluşur. Tek modüllü bir derlemede modül adı derleme adıyla aynıdır ve dosya adı modül adı artı bir uzantıdır.  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3. Bir sınıf tanımlayın. Bu örnekte, sınıfı olarak adlandırılır `Sample`.  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4. Yöntemine parametre adlarını içeren bir dize `Sample` dizisini geçirerek genel tür parametrelerini tanımlayın. <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> Bu, sınıfı genel bir tür yapar. Dönüş değeri, verilmiş kodunuzda kullanılabilen tür <xref:System.Reflection.Emit.GenericTypeParameterBuilder> parametrelerini temsil eden bir nesne dizisidir.  
  
     Aşağıdaki kodda, `Sample` tür parametreleri `TFirst` ve `TSecond`olan genel bir tür haline gelir. Kodu daha kolay okunabilir hale getirmek için, her <xref:System.Reflection.Emit.GenericTypeParameterBuilder> biri tür parametresiyle aynı ada sahip bir değişkene yerleştirilir.  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5. Tür parametrelerine özel kısıtlamalar ekleyin. Bu örnekte, tür parametresi `TFirst` parametresiz oluşturucular olan türlerle ve başvuru türlerine sınırlıdır.  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6. İsteğe bağlı olarak tür parametrelerine sınıf ve arabirim kısıtlamaları ekleyin. Bu örnekte, `TFirst` tür parametresi, değişkeninde <xref:System.Type> `baseType`bulunan nesnenin temsil ettiği temel sınıftan türetilmiş türler ile sınırlıdır ve türleri değişkenlerde ve `interfaceA` `interfaceB`değişkenleri içeren arabirimleri uygular. Bu değişkenlerin bildirimi ve atanması için kod örneğine bakın.  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7. Bir alan tanımlayın. Bu örnekte, alanın türü tür parametresiyle `TFirst`belirtilir. <xref:System.Reflection.Emit.GenericTypeParameterBuilder>' dan <xref:System.Type>türetilir, bu nedenle, genel tür parametrelerini bir tür kullanılabilir her yerde kullanabilirsiniz.  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8. Genel türün tür parametrelerini kullanan bir yöntem tanımlayın. Bu tür yöntemlerin, kendi tür parametre listelerine sahip olmadıkları müddetçe genel olmadığına unutmayın. Aşağıdaki kod, dizisi alan `static` `Shared` `TFirst` ve dizinin tüm öğelerini içeren bir `List<TFirst>` (`List(Of TFirst)` Visual Basic) döndüren bir yöntemi (Visual Basic) tanımlar. Bu yöntemi tanımlamak için, türü `List<TFirst>` genel tür tanımına çağırarak <xref:System.Type.MakeGenericType%2A> oluşturulması gerekir. `List<T>` (, `T` `typeof` İşleci kullandığınızda (`GetType` Visual Basic), genel tür tanımını almak için atlanır.) Parametre türü, <xref:System.Type.MakeArrayType%2A> yöntemi kullanılarak oluşturulur.  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. Yöntem gövdesini yay. Yöntem gövdesi, giriş dizisini yığına yükleyen üç opbebeden oluşur, `List<TFirst>` `IEnumerable<TFirst>` (girdi öğelerini listeye yerleştirme işini yapan) çağırır ve (yığında yeni <xref:System.Collections.Generic.List%601> nesneyi bırakır) döndürür. Bu kodu yayın zor kısmı oluşturucuyu alıyor.  
  
     <xref:System.Type.GetConstructor%2A> Yöntemi bir <xref:System.Reflection.Emit.GenericTypeParameterBuilder>üzerinde desteklenmez, bu nedenle `List<TFirst>` doğrudan oluşturucusunu almak mümkün değildir. İlk olarak, genel tür tanımının `List<T>` yapıcısını almak ve sonra karşılık gelen oluşturucusuna dönüştüren bir yöntemi çağırmak gereklidir. `List<TFirst>`  
  
     Bu kod örneği için kullanılan Oluşturucu bir `IEnumerable<T>`alır. Ancak, bunun <xref:System.Collections.Generic.IEnumerable%601> genel arabirimin genel tür tanımı olmadığına not edin; Bunun `T` yerine, öğesinden `List<T>` tür parametresi öğesinin `T` `IEnumerable<T>`tür parametresinin yerine gelmelidir. (Bu yalnızca, her iki tür de adlı `T`tür parametrelerine sahip olduğundan kafa karıştırıcı görünmektedir. Bu nedenle, bu kod örneği adları `TFirst` ve ' i `TSecond`kullanır.) Oluşturucu bağımsız değişkeninin türünü almak için, genel tür tanımıyla `IEnumerable<T>` başlayın ve ilk genel tür parametresiyle çağırın <xref:System.Type.MakeGenericType%2A> `List<T>`. Oluşturucu bağımsız değişken listesi, bu durumda yalnızca bir bağımsız değişken ile bir dizi olarak geçirilmelidir.  
  
    > [!NOTE]
    > Genel tür tanımı, C# ' de `IEnumerable<>` `typeof` işleci kullandığınızda veya `IEnumerable(Of )` `GetType` işleci Visual Basic kullandığınızda olarak ifade edilir.  
  
     Şimdi, genel tür tanımına çağırarak `List<T>` <xref:System.Type.GetConstructor%2A> yapıcısını almak mümkündür. Bu oluşturucuyu karşılık `List<TFirst>`gelen, `List<TFirst>` ve oluşturucusunu ' dan `List<T>` statik <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> yönteme dönüştürmek için.  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. Türü oluşturun ve dosyayı kaydedin.  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. Yöntemi çağırın. `ExampleMethod`Genel değildir, ancak onun ait olduğu tür geneldir, bu nedenle çağrılabilir bir <xref:System.Reflection.MethodInfo> tür oluşturmak için tür tanımından oluşturulmuş bir tür oluşturulması gerekir. `Sample` Oluşturulan tür, bir başvuru `Example` türü olduğu ve varsayılan parametresiz oluşturucusu ve `TFirst` üzerindeki `ExampleDerived` `TSecond`kısıtlamaları karşılayan sınıf olduğundan, kısıtlamalarını karşılayan sınıfını kullanır. (İçin `ExampleDerived` kod, örnek kod bölümünde bulunabilir.) Oluşturulan türü oluşturmak için bu iki <xref:System.Type.MakeGenericType%2A> tür öğesine geçirilir. Daha <xref:System.Reflection.MethodInfo> sonra <xref:System.Type.GetMethod%2A> yöntemi kullanılarak elde edilir.  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. Aşağıdaki kod bir `Example` nesne dizisi oluşturur, bu diziyi çağrılacak yöntemin bağımsız değişkenlerini temsil eden tür <xref:System.Object> dizisine koyar ve <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> yönteme geçirir. Yöntemi olduğundan, <xref:System.Reflection.MethodBase.Invoke%2A> yöntemin ilk bağımsız değişkeni null bir başvurudur `static`.  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, bir temel sınıf ve `Sample`iki arabirim ile birlikte adlı bir sınıfı tanımlar. Program için `Sample`iki genel tür parametresi tanımlar, genel bir türe dönüştürür. Tür parametreleri, bir türü genel yapan tek şeydir. Program, tür parametrelerinin tanımından önce ve sonra bir test iletisi görüntüleyerek bunu gösterir.  
  
 Tür parametresi `TSecond` , temel sınıf ve arabirimleri kullanarak sınıf ve arabirim kısıtlamalarını göstermek için kullanılır ve tür parametresi `TFirst` özel kısıtlamaları göstermek için kullanılır.  
  
 Kod örneği, alan türü için sınıfın tür parametrelerini ve yönteminin parametre ve dönüş türünü kullanarak bir alanı ve yöntemi tanımlar.  
  
 `Sample` Sınıf oluşturulduktan sonra yöntemi çağrılır.  
  
 Program, bir genel tür hakkındaki bilgileri ve bir tür parametresindeki özel kısıtlamaları listeleyen bir yöntemi içerir. Bu yöntemler, tamamlanan `Sample` sınıfla ilgili bilgileri göstermek için kullanılır.  
  
 Program, tamamlanmış modülünü diske kaydeder `GenericEmitExample1.dll`, bu nedenle onu [ıldadsm. exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) ile AÇABILIR ve `Sample` sınıfı için MSIL 'yi inceleyebilirsiniz.  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Emit.GenericTypeParameterBuilder>
- [Yansıma yayma kullanma](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))
- [Yansıma yayma dinamik derleme senaryoları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tt9483fk(v=vs.100))
