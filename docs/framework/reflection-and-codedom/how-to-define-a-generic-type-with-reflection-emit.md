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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8527f5f4a52c02744b02fea7ffaf833c223fa3f1
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65586215"
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a>Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama
Bu konu iki tür parametreleri ile basit bir genel tür oluşturma için tür parametreleri sınıf kısıtlamaları, arabirim kısıtlamasını ve özel kısıtlamalar uygulamak nasıl ve sınıf türü parametreler parametre türleri olarak kullanan üyeleri oluşturma işlemini gösterir. ve dönüş türleri.  
  
> [!IMPORTANT]
>  Bir yöntem genel değil, çünkü yalnızca genel bir türe ait ve bu türdeki tür parametreleri kullanır. Bir yalnızca kendi tür parametresi listesi varsa genel yöntemdir. Genel türlerde çoğu yöntemler, bu örnekte olduğu gibi genel değildir. Genel yöntem yayan bir örnek için bkz: [nasıl yapılır: Yansıma ile genel yöntem tanımlama yayma](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-method-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-type"></a>Genel bir tür tanımlamak için  
  
1. Adlı bir dinamik derleme tanımlama `GenericEmitExample1`. Bu örnekte, derleme yürütülen ve disk için bunu kaydedilmiş <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> belirtilir.  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2. Dinamik modül tanımlama. Bir derleme yürütülebilir modüllerin oluşur. Bir modül tek derleme için modül adını derleme adı ile aynıdır ve yanı sıra bir uzantı modül adı dosya adıdır.  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3. Bir sınıf tanımlar. Bu örnekte, sınıf adlı `Sample`.  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4. Genel tür parametrelerini tanımlayın `Sample` için parametre adlarını içeren bir dize dizisi geçirerek <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> yöntemi. Bu sınıf bir genel tür sağlar. Dönüş değeri bir dizisidir <xref:System.Reflection.Emit.GenericTypeParameterBuilder> yayılan kodunuzda kullanılabilecek tür parametreleri temsil eden nesneleri.  
  
     Aşağıdaki kodda, `Sample` tür parametreleri ile genel tür olur `TFirst` ve `TSecond`. Kod okumak her kolaylaştırmak için <xref:System.Reflection.Emit.GenericTypeParameterBuilder> tür parametresiyle aynı ada sahip bir değişken yerleştirilir.  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5. Özel kısıtlamalar için tür parametreleri ekleyin. Bu örnekte, tür parametresi `TFirst` parametresiz oluşturuculara sahip türleri ve başvuru türleri için sınırlıdır.  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6. İsteğe bağlı olarak, sınıf ve arabirim kısıtlamaları için tür parametreleri ekleyin. Bu örnekte, tür parametresi `TFirst` tarafından temsil edilen temel sınıftan türetilen türler için kısıtlı <xref:System.Type> değişkeninde bulunan nesne `baseType`, ve değişkenler eşleşen türleri bulunur arabirimler uygulama `interfaceA` ve `interfaceB`. Bu değişken ataması ve bildirimi için kod örneğe bakın.  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7. Bir alan tanımlayın. Bu örnekte, alan türü tür parametresi tarafından belirtilen `TFirst`. <xref:System.Reflection.Emit.GenericTypeParameterBuilder> öğesinden türetilen <xref:System.Type>, genel tür parametreleri türü kullanılabilir her yerde kullanabilirsiniz.  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8. Genel türün tür parametreleri kullanan bir yöntem tanımlayın. Kendi türü parametre listeleri sahip olmadıkları sürece bu tür yöntemler genel olmadığına dikkat edin. Aşağıdaki kodu tanımlayan bir `static` yöntemi (`Shared` Visual Basic'te) dizisi alır `TFirst` ve döndürür bir `List<TFirst>` (`List(Of TFirst)` Visual Basic'te) dizinin tüm öğeleri içeren. Bu yöntemi tanımlamak için türü oluşturmak için gerekli olduğu `List<TFirst>` çağırarak <xref:System.Type.MakeGenericType%2A> genel tür tanımı `List<T>`. ( `T` Kullandığınızda atlanırsa `typeof` işleci (`GetType` Visual Basic'te) genel tür tanımı alınamıyor.) Parametre türü kullanılarak oluşturulan <xref:System.Type.MakeArrayType%2A> yöntemi.  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. Yöntem gövdesini gösterin. Yöntem gövdesini yığına Giriş dizisinin yük üç işlem oluşur, çağrı `List<TFirst>` alan oluşturucu `IEnumerable<TFirst>` (hangi çalışır listeye giriş öğelerini yerleştirme tüm) ve döndürür (yeni bırakarak <xref:System.Collections.Generic.List%601> nesnesi Yığında). Bu kod yayan zor parçası Oluşturucu almaktır.  
  
     <xref:System.Type.GetConstructor%2A> Üzerinde yöntemi desteklenmiyor bir <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, oluşturucusunun almak mümkün olmadığından `List<TFirst>` doğrudan. İlk olarak, genel tür tanımı oluşturucusunun almak gerekli olan `List<T>` ve karşılık gelen oluşturucusuna dönüştüren bir yöntemi çağırmak için `List<TFirst>`.  
  
     Bu kod örneği için kullanılan oluşturucuya alan bir `IEnumerable<T>`. Ancak, bu genel tür tanımı olmadığını unutmayın <xref:System.Collections.Generic.IEnumerable%601> genel arabirim; bunun yerine, tür parametresi `T` gelen `List<T>` tür parametresi yerine `T` , `IEnumerable<T>`. (Yalnızca iki türü de adlı türü parametreleri olduğundan, bu karmaşık görünüyor `T`. Bu kod örneği adları kullanan neden that is `TFirst` ve `TSecond`.) Oluşturucu bağımsız değişken türünü almak için genel tür tanımı ile Başlat `IEnumerable<T>` ve çağrı <xref:System.Type.MakeGenericType%2A> ilk genel tür parametresi ile `List<T>`. Oluşturucu bağımsız değişken listesi ile tek bağımsız değişken bir dizi olarak bu durumda geçirilmelidir.  
  
    > [!NOTE]
    >  Genel tür tanımı olarak ifade edilen `IEnumerable<>` kullandığınızda `typeof` C# ' ta, işleci veya `IEnumerable(Of )` kullandığınızda `GetType` Visual Basic'te işleci.  
  
     Şimdi oluşturucusu, alma olasılığı `List<T>` çağırarak <xref:System.Type.GetConstructor%2A> genel tür tanımı. Bu oluşturucu karşılık gelen oluşturucuya dönüştürmek için `List<TFirst>`, geçmesi `List<TFirst>` ve oluşturucudan `List<T>` statik <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> yöntemi.  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. Türü oluşturun ve dosyayı kaydedin.  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. Yöntemi çağır. `ExampleMethod` Genel, değil ancak ait olduğu için tür şekilde alabilmek için genel bir <xref:System.Reflection.MethodInfo> , çağrılacak oluşturulan tür için tür tanımı oluşturmak gerekli olan `Sample`. Oluşturulan tür kullanan `Example` üzerindeki kısıtlamalar karşılayan sınıfı `TFirst` bir başvuru türüdür ve varsayılan parametresiz bir oluşturucu olduğundan ve `ExampleDerived` üzerindeki kısıtlamalar karşılayan sınıfı `TSecond`. (Kodu `ExampleDerived` örnek kod bölümünde bulunabilir.) Bu iki tür geçirilen <xref:System.Type.MakeGenericType%2A> oluşturulmuş türü oluşturmak için. <xref:System.Reflection.MethodInfo> Ardından kullanılarak elde edilen <xref:System.Type.GetMethod%2A> yöntemi.  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. Aşağıdaki kod bir dizi oluşturur `Example` nesneleri, bu dizi türünde bir dizi yerleştirir <xref:System.Object> çağrılacak, yöntemin bağımsız değişkenlerini temsil eden ve bunları geçirmeden <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> yöntemi. İlk bağımsız değişkeni <xref:System.Reflection.MethodBase.Invoke%2A> bir null başvuru yöntemdir yöntemi olduğundan `static`.  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde adlı bir sınıf tanımlar `Sample`, yanı sıra bir taban sınıfı ve iki arabirim. Program iki genel tür parametrelerini tanımlar `Sample`, genel bir tür kapatma. Tür, genel bir tür yaptığı tek şey parametrelerdir. Program bu sınama iletisi görüntüleyerek önce ve sonra tür parametreleri tanımını gösterir.  
  
 Tür parametresi `TSecond` temel sınıf ve arabirimler ve tür parametresi kullanarak, sınıf ve arabirim kısıtlamaları göstermek için kullanılan `TFirst` özel kısıtlamaları göstermek için kullanılır.  
  
 Kod örneği, bir alan ve alan türü ve parametre sınıfın tür parametreleri kullanarak yöntemi tanımlar ve dönüş türü yöntemi.  
  
 Sonra `Sample` sınıf oluşturuldu, yöntemi çağrılır.  
  
 Program, genel bir tür hakkında bilgi listeleyen bir yöntem ve özel bir tür parametresi kısıtlamaları listeleyen bir yöntem içerir. Bu yöntemler tamamlanmış hakkındaki bilgileri görüntülemek için kullanılan `Sample` sınıfı.  
  
 Program tamamlanmış modülü diske kaydeder. `GenericEmitExample1.dll`, kendisiyle açabilmek [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ve incelemek için MSIL `Sample` sınıfı.  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Emit.GenericTypeParameterBuilder>
- [Yansıma yaymanın](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/3y322t50(v=vs.100))
- [Yansıma yayma dinamik derleme senaryoları](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/tt9483fk(v=vs.100))
