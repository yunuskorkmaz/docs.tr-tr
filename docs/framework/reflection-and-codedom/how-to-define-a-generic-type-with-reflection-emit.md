---
title: "Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- generics [.NET Framework], dynamic types
- reflection emit, generic types
ms.assetid: 07d5f01a-7b5b-40ea-9b15-f21561098fe4
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d6096a54c6a530035bd32c24d427ba047f905476
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-define-a-generic-type-with-reflection-emit"></a>Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama
Bu konuda iki tür parametreleri ile basit bir genel tür oluşturma, tür parametreleri sınıf kısıtlamaları, arabirim kısıtlamaları ve özel kısıtlamalar uygulamak nasıl ve parametre türleri olarak sınıfın türü parametreleri kullanma üyeleri oluşturmak üzere nasıl gösterir ve dönüş türleri.  
  
> [!IMPORTANT]
>  Yalnızca genel bir tür ait ve bu tür tür parametreleri kullanan bir yöntem genel olmadığından. Yalnızca kendi türü parametre listesine varsa genel yöntemidir. Genel türler çoğu yöntemlere genel bu örnekteki değildir. Genel yöntem yayma ilişkin bir örnek için bkz: [nasıl yapılır: yansıma yayma ile genel yöntem tanımlama](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-method-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-type"></a>Genel bir tür tanımlamak için  
  
1.  Adlı bir dinamik derleme tanımlamak `GenericEmitExample1`. Bu örnekte, derleme yürütülen ve diske, bunu kaydedilmiş <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> belirtilir.  
  
     [!code-cpp[EmitGenericType#2](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#2)]
     [!code-csharp[EmitGenericType#2](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#2)]
     [!code-vb[EmitGenericType#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#2)]  
  
2.  Dinamik bir modül tanımlayın. Bir derlemeyi yürütülebilir modüllerini yapılır. Bir tek modül derlemesi için modül adı derleme adı ile aynıdır ve modül adına artı bir uzantısı dosya adıdır.  
  
     [!code-cpp[EmitGenericType#3](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#3)]
     [!code-csharp[EmitGenericType#3](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#3)]
     [!code-vb[EmitGenericType#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#3)]  
  
3.  Bir sınıf tanımlayın. Bu örnekte adlı sınıfı `Sample`.  
  
     [!code-cpp[EmitGenericType#4](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#4)]
     [!code-csharp[EmitGenericType#4](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#4)]
     [!code-vb[EmitGenericType#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#4)]  
  
4.  Genel tür parametreleri tanımla `Sample` parametrelerinin adlarını içeren bir dizeler dizisi geçirerek <xref:System.Reflection.Emit.TypeBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> yöntemi. Bu genel bir tür sınıfı sağlar. Dönüş değeri dizisidir <xref:System.Reflection.Emit.GenericTypeParameterBuilder> verilmiş kodunuzda kullanılabilir tür parametreleri temsil eden nesne.  
  
     Aşağıdaki kodda, `Sample` tür parametreleri ile genel tür hale `TFirst` ve `TSecond`. Kod okumak her kolaylaştırmak için <xref:System.Reflection.Emit.GenericTypeParameterBuilder> tür parametresi aynı ada sahip bir değişken yerleştirilir.  
  
     [!code-cpp[EmitGenericType#5](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#5)]
     [!code-csharp[EmitGenericType#5](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#5)]
     [!code-vb[EmitGenericType#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#5)]  
  
5.  Özel kısıtlamalar tür parametreleri ekleyin. Bu örnekte, tür parametresi `TFirst` parametresiz oluşturucular türleri ve başvuru türleri için sınırlı değildir.  
  
     [!code-cpp[EmitGenericType#6](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#6)]
     [!code-csharp[EmitGenericType#6](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#6)]
     [!code-vb[EmitGenericType#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#6)]  
  
6.  İsteğe bağlı olarak sınıfı ve arabirim kısıtlamaları tür parametreleri ekleyin. Bu örnekte, tür parametresi `TFirst` tarafından temsil edilen temel sınıfından türetilen türler için kısıtlı <xref:System.Type> değişkende nesnelere `baseType`, ve değişkenleri olan türleri bulunur arabirimleri uygulama `interfaceA` ve `interfaceB`. Bu değişkenlerin ataması ve bildirimi kod örneğine bakın.  
  
     [!code-cpp[EmitGenericType#7](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#7)]
     [!code-csharp[EmitGenericType#7](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#7)]
     [!code-vb[EmitGenericType#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#7)]  
  
7.  Bir alan tanımlayın. Bu örnekte, alan türü tür parametresi tarafından belirtilen `TFirst`. <xref:System.Reflection.Emit.GenericTypeParameterBuilder>türetilen <xref:System.Type>, genel tür parametreleri bir türü kullanılabilir herhangi bir yerde kullanabilirsiniz.  
  
     [!code-cpp[EmitGenericType#21](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#21)]
     [!code-csharp[EmitGenericType#21](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#21)]
     [!code-vb[EmitGenericType#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#21)]  
  
8.  Genel tür türü parametreleri kullanan bir yöntem tanımlayın. Kendi türü parametre listeleri sahip oldukları sürece bu tür yöntemleri genel olmadığına dikkat edin. Aşağıdaki kodu tanımlayan bir `static` yöntemi (`Shared` Visual Basic'te) bir dizi alan `TFirst` ve döndürür bir `List<TFirst>` (`List(Of TFirst)` Visual Basic'te) dizinin tüm öğeleri içeren. Bu yöntem tanımlamak için bu türü oluşturmak gerekli olan `List<TFirst>` çağırarak <xref:System.Type.MakeGenericType%2A> genel tür tanımında `List<T>`. ( `T` Kullandığınızda atlanmış `typeof` işleci (`GetType` Visual Basic'te) genel tür tanımı alınamıyor.) Parametre türü kullanılarak oluşturulan <xref:System.Type.MakeArrayType%2A> yöntemi.  
  
     [!code-cpp[EmitGenericType#22](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#22)]
     [!code-csharp[EmitGenericType#22](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#22)]
     [!code-vb[EmitGenericType#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#22)]  
  
9. Yöntem gövdesi yayma. Giriş dizisi yığına yük üç işlem kodları yöntem gövdesi oluşur, çağrı `List<TFirst>` alan oluşturucu `IEnumerable<TFirst>` (hangi yaptığı tüm iş girişi öğelerinin listeye yerleştirme) ve döndürme (yeni bırakarak <xref:System.Collections.Generic.List%601> nesnesi Yığında). Bu kod yayma zor bir kısmını Oluşturucusu almaktır.  
  
     <xref:System.Type.GetConstructor%2A> Yöntemi desteklenmiyor bir <xref:System.Reflection.Emit.GenericTypeParameterBuilder>, oluşturucusunun almak mümkün değildir `List<TFirst>` doğrudan. İlk olarak, genel tür tanımında Oluşturucusu almak gerekli olan `List<T>` ve ardından karşılık gelen oluşturucusuna dönüştüren bir yöntemi çağırmak için `List<TFirst>`.  
  
     Bu kod örneği için kullanılan Oluşturucu geçen bir `IEnumerable<T>`. Ancak, bu genel tür tanımı olmadığını unutmayın <xref:System.Collections.Generic.IEnumerable%601> genel arabirim; bunun yerine, tür parametresi `T` gelen `List<T>` tür parametresi için yerine `T` , `IEnumerable<T>`. (Yalnızca her iki tür adlı türü parametrelerine sahip olduğundan, bu kafa karıştırıcı görünüyor `T`. Bu kod örneği adları kullanır neden that is `TFirst` ve `TSecond`.) Oluşturucu bağımsız değişkeni tür almak için genel tür tanımıyla Başlat `IEnumerable<T>` ve arama <xref:System.Type.MakeGenericType%2A> ilk genel tür parametresi ile `List<T>`. Oluşturucu bağımsız değişken listesi tek bağımsız değişkenli bir dizi olarak bu durumda geçirilmelidir.  
  
    > [!NOTE]
    >  Genel tür tanımı olarak ifade edilen `IEnumerable<>` kullandığınızda `typeof` C# ' ta, işleci veya `IEnumerable(Of )` kullandığınızda `GetType` Visual Basic'te işleci.  
  
     Oluşturucusunun almak mümkün şimdi `List<T>` çağırarak <xref:System.Type.GetConstructor%2A> genel tür tanımında. Bu oluşturucu karşılık gelen oluşturucuya dönüştürmek için `List<TFirst>`, geçirmek `List<TFirst>` ve oluşturucudan `List<T>` statik <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29?displayProperty=nameWithType> yöntemi.  
  
     [!code-cpp[EmitGenericType#23](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#23)]
     [!code-csharp[EmitGenericType#23](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#23)]
     [!code-vb[EmitGenericType#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#23)]  
  
10. Türü oluşturun ve dosyayı kaydedin.  
  
     [!code-cpp[EmitGenericType#8](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#8)]
     [!code-csharp[EmitGenericType#8](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#8)]
     [!code-vb[EmitGenericType#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#8)]  
  
11. Invoke yöntemi. `ExampleMethod`Genel, değil ancak ait olduğu için tür böylece alabilmek için genel bir <xref:System.Reflection.MethodInfo> , çağrılabilir yapılandırılmış bir tür için tür tanımı oluşturmak gerekli olan `Sample`. Yapılandırılmış bir tür kullanıyor `Example` üzerindeki kısıtlamaları karşılayan sınıfı `TFirst` bir başvuru türü olduğundan ve varsayılan parametresiz oluşturucusu olan ve `ExampleDerived` üzerindeki kısıtlamaları karşılayan sınıfı `TSecond`. (Kodunu `ExampleDerived` örnek kod bölümünde bulunabilir.) Bu iki tür geçirilecek <xref:System.Type.MakeGenericType%2A> oluşturulan türü oluşturun. <xref:System.Reflection.MethodInfo> Kullanılarak elde edilir <xref:System.Type.GetMethod%2A> yöntemi.  
  
     [!code-cpp[EmitGenericType#9](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#9)]
     [!code-csharp[EmitGenericType#9](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#9)]
     [!code-vb[EmitGenericType#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#9)]  
  
12. Aşağıdaki kod bir dizi oluşturur `Example` nesneleri, bu dizi türünde bir dizi yerleştirir <xref:System.Object> çağrılacak, yöntemin bağımsız değişkenleri temsil eden ve bunlara geçirir <xref:System.Reflection.MethodBase.Invoke%28System.Object%2CSystem.Object%5B%5D%29> yöntemi. İlk bağımsız değişkeni <xref:System.Reflection.MethodBase.Invoke%2A> yöntemi bir null başvuru yöntemi açık olduğundan `static`.  
  
     [!code-cpp[EmitGenericType#10](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#10)]
     [!code-csharp[EmitGenericType#10](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#10)]
     [!code-vb[EmitGenericType#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#10)]  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde adlı bir sınıf tanımlar `Sample`, bir taban sınıf ve iki arabirim yanı sıra. Program için iki genel tür parametreleri tanımlar `Sample`, genel bir tür kapatma. Türü, bir tür genel yapar tek şey parametreleridir. Program bu önce ve sonra tür parametreleri tanımını sınama iletisi görüntüleyerek gösterir.  
  
 Tür parametresi `TSecond` temel sınıf ve arabirimler ve tür parametresi kullanılarak, sınıf ve arabirim kısıtlamaları göstermek için kullanılan `TFirst` özel kısıtlamalar göstermek için kullanılır.  
  
 Kod örneği, bir alan ve alan türü ve parametresi için sınıfının tür parametreleri kullanarak yöntemi tanımlar ve yöntem türü döndürür.  
  
 Sonra `Sample` sınıfı oluşturulamadı, yöntemi çağrılır.  
  
 Program, genel bir tür hakkında bilgileri listeleyen bir yöntem ve bir tür parametresi özel kısıtlamalar listeleyen yöntemi içerir. Bu yöntemler tamamlanmış hakkındaki bilgileri görüntülemek için kullanılan `Sample` sınıfı.  
  
 Program tamamlanmış modülü diske kaydeder `GenericEmitExample1.dll`, kendisiyle açabilmesi için [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) ve incelemek için MSIL `Sample` sınıfı.  
  
 [!code-cpp[EmitGenericType#1](../../../samples/snippets/cpp/VS_Snippets_CLR/EmitGenericType/CPP/source.cpp#1)]
 [!code-csharp[EmitGenericType#1](../../../samples/snippets/csharp/VS_Snippets_CLR/EmitGenericType/CS/source.cs#1)]
 [!code-vb[EmitGenericType#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/EmitGenericType/VB/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   C# kodunu `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.  
  
-   Hiçbir ek derleme başvurularını gereklidir.  
  
-   Csc.exe, vbc.exe veya cl.exe kullanarak komut satırında kodu derleyin. Visual Studio'da Kodu derlemek için bir konsol uygulama projesi şablonunda yerleştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.Emit.GenericTypeParameterBuilder>  
 [Yansıma kullanarak yayma](http://msdn.microsoft.com/library/ccc6540d-0e2c-4d89-b456-eb7353f9e9ac)  
 [Yansıma yayma dinamik derleme senaryoları](http://msdn.microsoft.com/library/e1cc6750-e20f-473b-bb4e-f43bc66aecce)
