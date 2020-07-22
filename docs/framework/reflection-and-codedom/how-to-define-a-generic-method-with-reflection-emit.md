---
title: 'Nasıl yapılır: Yansıma Yayma ile Genel Yöntem Tanımlama'
description: Yansıma Yayma ile genel bir yöntem tanımlayın. Bir örnek, iki tür parametresiyle genel bir yöntem oluşturur. İkinci bir örnek, Yöntem gövdesinin nasıl yayalınacağını gösterir.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic methods
- generics [.NET Framework], dynamic types
ms.assetid: 93892fa4-90b3-4ec4-b147-4bec9880de2b
ms.openlocfilehash: 3b85fb480e5862daa3b2800f75392adbe92348f2
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865144"
---
# <a name="how-to-define-a-generic-method-with-reflection-emit"></a>Nasıl yapılır: Yansıma Yayma ile Genel Yöntem Tanımlama

İlk yordam, iki tür parametresiyle basit bir genel yöntemin nasıl oluşturulacağını ve sınıf kısıtlamalarının, arabirim kısıtlamalarının ve özel kısıtlamaların tür parametrelerine nasıl uygulanacağını gösterir.

İkinci yordam, Yöntem gövdesinin nasıl yayılacağını ve genel türlerin örneklerini oluşturmak ve yöntemlerini çağırmak için genel yöntemin tür parametrelerinin nasıl kullanılacağını gösterir.

Üçüncü yordam genel yöntemin nasıl çağıralınacağını gösterir.

> [!IMPORTANT]
> Yalnızca genel bir türe ait olduğundan ve bu türün tür parametrelerini kullandığından bir yöntem genel değildir. Bir yöntem, yalnızca kendi tür parametresi listesine sahipse geneldir. Genel bir yöntem, bu örnekte olduğu gibi genel olmayan bir tür üzerinde bulunabilir. Genel türde genel olmayan bir metoda örnek için bkz. [nasıl yapılır: yansıma yayma Ile genel tür tanımlama](how-to-define-a-generic-type-with-reflection-emit.md).

### <a name="to-define-a-generic-method"></a>Genel bir yöntemi tanımlamak için

1. Başlamadan önce, üst düzey bir dil kullanılarak yazıldığında genel yöntemin nasıl göründüğünü bakmak yararlı olur. Aşağıdaki kod, genel yöntemi çağırmak için kod ile birlikte bu konunun örnek koduna dahildir. Yöntemi iki tür parametresine sahiptir `TInput` ve `TOutput` ikinci öğesinin bir başvuru türü () olması gereken, `class` parametresiz bir oluşturucuya () sahip olması `new` ve uygulaması gerekir `ICollection(Of TInput)` ( `ICollection<TInput>` C# ' de). Bu arabirim kısıtlaması, yönteminin <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> `TOutput` , yöntemin oluşturduğu koleksiyona öğe eklemek için kullanılmasını sağlar. Yönteminde, bir dizisi olan bir biçimsel parametre vardır `input` `TInput` . Yöntemi, türünde bir koleksiyon oluşturur `TOutput` ve öğelerini `input` koleksiyona kopyalar.

    [!code-csharp[GenericMethodHowTo#20](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#20)]
    [!code-vb[GenericMethodHowTo#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#20)]

2. Genel yöntemin ait olduğu türü içeren bir dinamik derleme ve dinamik modül tanımlayın. Bu durumda, derleme yalnızca bir modüle sahiptir `DemoMethodBuilder1` ve modül adı derleme adının yanı sıra bir uzantıyla aynıdır. Bu örnekte, derleme diske kaydedilir ve de yürütülür, bu nedenle <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> belirtilir. DemoMethodBuilder1.dll incelemek ve adım 1 ' de gösterilen metodun Microsoft ara dili (MSIL) ile karşılaştırmak için [Ildasm.exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.

    [!code-csharp[GenericMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#2)]
    [!code-vb[GenericMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#2)]

3. Genel yöntemin ait olduğu türü tanımlayın. Türün genel olması gerekmez. Genel bir yöntem genel ya da genel olmayan bir türe ait olabilir. Bu örnekte, tür bir sınıftır, genel değildir ve adlandırılır `DemoType` .

    [!code-csharp[GenericMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#3)]
    [!code-vb[GenericMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#3)]

4. Genel yöntemi tanımlayın. Genel yöntemin biçimsel parametrelerinin türleri genel yöntemin genel tür parametreleriyle belirtilmişse, <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%28System.String%2CSystem.Reflection.MethodAttributes%29> yöntemi tanımlamak için yöntem aşırı yüklemesini kullanın. Metodun genel tür parametreleri henüz tanımlı değil, bu nedenle, çağrısındaki metodun biçimsel parametrelerinin türlerini belirtemezsiniz <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%2A> . Bu örnekte, yöntemi olarak adlandırılmıştır `Factory` . Yöntemi geneldir ve `static` ( `Shared` Visual Basic).

    [!code-csharp[GenericMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#4)]
    [!code-vb[GenericMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#4)]

5. `DemoMethod`Yöntemine parametre adlarını içeren bir dize dizisini geçirerek genel tür parametrelerini tanımlayın <xref:System.Reflection.Emit.MethodBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> . Bu, yöntemi genel bir yöntem yapar. Aşağıdaki kod, `Factory` tür parametreleri ve olan genel bir yöntem `TInput` oluşturur `TOutput` . Kodu daha kolay okunabilir hale getirmek için, bu adlara sahip değişkenler, <xref:System.Reflection.Emit.GenericTypeParameterBuilder> iki tür parametresini temsil eden nesneleri tutmak üzere oluşturulur.

    [!code-csharp[GenericMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#5)]
    [!code-vb[GenericMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#5)]

6. İsteğe bağlı olarak tür parametrelerine özel kısıtlamalar ekleyin. Özel kısıtlamalar yöntemi kullanılarak eklenir <xref:System.Reflection.Emit.GenericTypeParameterBuilder.SetGenericParameterAttributes%2A> . Bu örnekte, `TOutput` bir başvuru türü ve parametresiz bir oluşturucuya sahip olmak için kısıtlanmıştır.

    [!code-csharp[GenericMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#6)]
    [!code-vb[GenericMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#6)]

7. İsteğe bağlı olarak tür parametrelerine sınıf ve arabirim kısıtlamaları ekleyin. Bu örnekte, tür parametresi `TOutput` `ICollection(Of TInput)` ( `ICollection<TInput>` C# ' de) arabirimini uygulayan türlerle sınırlıdır. Bu <xref:System.Collections.Generic.ICollection%601.Add%2A> Yöntem, yöntemin öğe eklemek için kullanılmasını sağlar.

    [!code-csharp[GenericMethodHowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#7)]
    [!code-vb[GenericMethodHowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#7)]

8. Yöntemini kullanarak yönteminin biçimsel parametrelerini tanımlayın <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> . Bu örnekte, yönteminin bir `Factory` dizisi olan bir parametresi vardır `TInput` . Bu tür <xref:System.Type.MakeArrayType%2A> , öğesini temsil eden üzerinde yöntemi çağırarak oluşturulur <xref:System.Reflection.Emit.GenericTypeParameterBuilder> `TInput` . Bağımsız değişkeni <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> bir <xref:System.Type> nesne dizisidir.

    [!code-csharp[GenericMethodHowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#8)]
    [!code-vb[GenericMethodHowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#8)]

9. Yöntemini kullanarak yöntemi için dönüş türünü tanımlayın <xref:System.Reflection.Emit.MethodBuilder.SetReturnType%2A> . Bu örnekte, bir örneği `TOutput` döndürülür.

    [!code-csharp[GenericMethodHowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#9)]
    [!code-vb[GenericMethodHowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#9)]

10. Yöntemini kullanarak Yöntem gövdesini yay <xref:System.Reflection.Emit.ILGenerator> . Ayrıntılar için bkz. Yöntem gövdesini yayma için eşlik eden yordam.

    > [!IMPORTANT]
    > Çağrıları genel türdeki yöntemlere yaydığınızda ve bu türlerin tür bağımsız değişkenleri genel yöntemin tür parametreleridir, `static` <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29> <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> <xref:System.Reflection.Emit.TypeBuilder.GetField%28System.Type%2CSystem.Reflection.FieldInfo%29> <xref:System.Reflection.Emit.TypeBuilder> yöntemlerin oluşturulmuş biçimlerini almak için sınıfının, ve Yöntem yüklerini kullanmanız gerekir. Yöntem gövdesini yayma yordamı bunu gösterir.

11. Yöntemini içeren türü doldurun ve derlemeyi kaydedin. Genel yöntemi çağırmak için eşlik eden yordam, tamamlanmış yöntemi çağırmak için iki yol gösterir.

    [!code-csharp[GenericMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#14)]
    [!code-vb[GenericMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#14)]

<a name="procedureSection1"></a>

### <a name="to-emit-the-method-body"></a>Yöntem gövdesini yayma

1. Bir kod Oluşturucu alın ve yerel değişkenleri ve etiketleri bildirin. <xref:System.Reflection.Emit.ILGenerator.DeclareLocal%2A>Yöntemi yerel değişkenleri bildirmek için kullanılır. `Factory`Yöntemi dört yerel değişkene sahiptir: `retVal` `TOutput` yöntemi tarafından döndürülen yeni ' yi tutmak, `ic` `TOutput` `ICollection(Of TInput)` `ICollection<TInput>` `input` nesne giriş dizisini tutmak `TInput` ve dizi boyunca yinelemek için, yöntemini (C# ' ta) `index` tutmak için. Bu yöntemde, bir, bir diğeri ( `enterLoop` ) ve bir diğeri (), `loopAgain` yöntemi kullanılarak tanımlanan döngü () için iki etiket vardır <xref:System.Reflection.Emit.ILGenerator.DefineLabel%2A> .

    İlk şey yöntemi Opcode kullanarak bağımsız değişkenini yüklemek <xref:System.Reflection.Emit.OpCodes.Ldarg_0> ve Opcode kullanarak yerel değişkende depolamak `input` <xref:System.Reflection.Emit.OpCodes.Stloc_S> .

    [!code-csharp[GenericMethodHowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#10)]
    [!code-vb[GenericMethodHowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#10)]

2. `TOutput`Yönteminin genel yöntem aşırı yüklemesini kullanarak bir örneğini oluşturmak için kodu yay <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> . Bu aşırı yüklemeyi kullanmak, belirtilen türün parametresiz bir oluşturucuya sahip olmasını gerektirir ve bu kısıtlamayı öğesine ekleme nedenidir `TOutput` . Öğesine geçirerek oluşturulan genel yöntemi oluşturun `TOutput` <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> . Yöntemi çağırmak için kodu gönderdikten sonra, kullanarak kodu yerel değişkende depolayın `retVal`<xref:System.Reflection.Emit.OpCodes.Stloc_S>

    [!code-csharp[GenericMethodHowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#11)]
    [!code-vb[GenericMethodHowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#11)]

3. Yeni `TOutput` nesneyi atamak `ICollection(Of TInput)` ve yerel değişkende saklamak için kodu yay `ic` .

    [!code-csharp[GenericMethodHowTo#31](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#31)]
    [!code-vb[GenericMethodHowTo#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#31)]

4. <xref:System.Reflection.MethodInfo>Yöntemi temsil edin <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> . Yöntemi bir `ICollection(Of TInput)` ( `ICollection<TInput>` C# ' ta) üzerinde davranıyor, bu nedenle, `Add` Bu oluşturulmuş türe özgü yöntemi almak için gereklidir. <xref:System.Type.GetMethod%2A> <xref:System.Reflection.MethodInfo> `icollOfTInput` <xref:System.Type.GetMethod%2A> İle oluşturulmuş bir tür üzerinde desteklenmediğinden, bunu doğrudan ' den almak için yöntemini kullanamazsınız <xref:System.Reflection.Emit.GenericTypeParameterBuilder> . Bunun yerine, <xref:System.Type.GetMethod%2A> `icoll` Genel arabirim için genel tür tanımını içeren öğesini çağırın <xref:System.Collections.Generic.ICollection%601> . Daha sonra <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> `static` , oluşturulan tür için oluşturmak için yöntemini kullanın <xref:System.Reflection.MethodInfo> . Aşağıdaki kod bunu gösterir.

    [!code-csharp[GenericMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#12)]
    [!code-vb[GenericMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#12)]

5. `index`32 bitlik bir tamsayı yükleyerek ve bunu değişkende depolayarak değişkeni başlatmak için kodu yay. Kodu Dala Dala yay `enterLoop` . Bu etiket, döngünün içinde olduğundan henüz işaretlenmedi. Döngü kodu bir sonraki adımda yayılır.

    [!code-csharp[GenericMethodHowTo#32](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#32)]
    [!code-vb[GenericMethodHowTo#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#32)]

6. Döngü için kod yay. İlk adım, etiketiyle çağırarak döngünün en üstünü işaretlemenize neden olur <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> `loopAgain` . Etiketi kullanan dal deyimleri artık koddaki bu noktaya dallandıracaktır. Bir sonraki adım, `TOutput` nesnesini yığına itmeniz, nesneye dönüştürmelisiniz `ICollection(Of TInput)` . Hemen gerekli değildir, ancak yöntemini çağırmak için konumunda olması gerekir `Add` . Giriş dizisi bir sonraki yığına gönderilir ve sonra `index` dizideki geçerli dizini içeren değişken. <xref:System.Reflection.Emit.OpCodes.Ldelem>Opcode dizin ve diziyi yığın dışına çıkarır ve dizinli dizi öğesini yığına gönderir. Yığın artık yöntemi çağrısı için hazırdır <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> . Bu, koleksiyonu ve yeni öğeyi yığının dışına çıkarır ve öğeyi koleksiyona ekler.

    Döngüdeki kodun geri kalanı dizini arttırır ve döngünün tamamlanıp bitmediğini görmek için sınar: Dizin ve 32 bitlik bir tamsayı 1 yığına gönderilir ve yığında toplamı bırakır; Toplam, içinde depolanır `index` . <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A>Bu noktayı döngünün giriş noktası olarak ayarlamak için çağırılır. Dizin yeniden yüklendi. Giriş dizisi yığına gönderilir ve <xref:System.Reflection.Emit.OpCodes.Ldlen> uzunluğunu almak için yayılır. Dizin ve uzunluk artık yığında bulunur ve <xref:System.Reflection.Emit.OpCodes.Clt> bunları karşılaştırmaya yönelik olarak yayılır. Dizin uzunluktan küçükse, <xref:System.Reflection.Emit.OpCodes.Brtrue_S> döngünün başlangıcına geri dallanma.

    [!code-csharp[GenericMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#13)]
    [!code-vb[GenericMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#13)]

7. `TOutput`Nesneyi yığına göndermek ve yönteminden döndürmek için kodu yay. Yerel değişkenler `retVal` ve `ic` her ikisi de yeni başvuru içerir `TOutput` ; `ic` yalnızca yöntemine erişmek için kullanılır <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> .

    [!code-csharp[GenericMethodHowTo#33](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#33)]
    [!code-vb[GenericMethodHowTo#33](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#33)]

<a name="procedureSection2"></a>

### <a name="to-invoke-the-generic-method"></a>Genel yöntemi çağırmak için

1. `Factory`genel bir yöntem tanımıdır. Çağırmak için, türleri genel tür parametrelerine atamanız gerekir. <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>Bunu yapmak için yöntemini kullanın. Aşağıdaki kod, <xref:System.String> `TInput` için ve Için (C# ' de) belirterek oluşturulmuş bir genel yöntem oluşturur `List(Of String)` `List<string>` `TOutput` ve yönteminin bir dize gösterimini görüntüler.

    [!code-csharp[GenericMethodHowTo#21](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#21)]
    [!code-vb[GenericMethodHowTo#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#21)]

2. Geç bağlantılı yöntemi çağırmak için <xref:System.Reflection.MethodBase.Invoke%2A> yöntemini kullanın. Aşağıdaki kod, <xref:System.Object> tek öğesi bir dize dizisi olarak içeren öğesinin bir dizisini oluşturur ve bunu genel yöntem için bağımsız değişken listesi olarak geçirir. Yöntemi olduğundan, ilk parametresi <xref:System.Reflection.MethodBase.Invoke%2A> null bir başvurudur `static` . Dönüş değeri öğesine `List(Of String)` ve ilk öğesi görüntülenir.

    [!code-csharp[GenericMethodHowTo#22](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#22)]
    [!code-vb[GenericMethodHowTo#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#22)]

3. Bir temsilciyi kullanarak yöntemi çağırmak için, oluşturulan genel yöntemin imzasıyla eşleşen bir temsilciye sahip olmanız gerekir. Bunu yapmanın kolay bir yolu, genel bir temsilci oluşturmaktır. Aşağıdaki kod, `D` yöntem aşırı yüklemesini kullanarak örnek kodda tanımlanan genel temsilcinin bir örneğini oluşturur <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType> ve temsilciyi çağırır. Temsilciler, geç bağlantılı çağrılara göre daha iyi gerçekleştirir.

    [!code-csharp[GenericMethodHowTo#23](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#23)]
    [!code-vb[GenericMethodHowTo#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#23)]

4. Yayınlanan Yöntem, kaydedilen derlemeye başvuran bir programdan de çağrılabilir.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, genel bir yöntemi olan genel olmayan bir tür oluşturur `DemoType` `Factory` . Bu yöntemin, `TInput` bir giriş türü belirtmek ve `TOutput` bir çıkış türü belirtmek için iki genel tür parametresi vardır. `TOutput`Tür parametresi, `ICollection<TInput>` ( `ICollection(Of TInput)` Visual Basic olarak), başvuru türü ve parametresiz bir oluşturucuya sahip olmak için sınırlandırılır.

Yönteminde bir dizisi olan bir biçimsel parametre vardır `TInput` . Yöntemi, `TOutput` giriş dizisinin tüm öğelerini içeren bir örneğini döndürür. `TOutput`genel arabirimi uygulayan herhangi bir genel koleksiyon türü olabilir <xref:System.Collections.Generic.ICollection%601> .

Kod yürütüldüğünde, dinamik derleme DemoGenericMethod1.dll olarak kaydedilir ve [Ildasm.exe (Il ayrıştırma)](../tools/ildasm-exe-il-disassembler.md)kullanılarak incelenebilir.

> [!NOTE]
> Kodu nasıl yayılacağınızı öğrenmek, oluşturmaya çalıştığınız görevi gerçekleştiren bir Visual Basic, C# veya Visual C++ programını yazmak ve derleyici tarafından üretilen MSIL 'yi incelemek için ayrıştırıcı 'yi kullanmak için iyi bir yoldur.

Kod örneği, yayılan yönteme denk gelen kaynak kodunu içerir. Yayınlanan Yöntem, geç ve ayrıca kod örneğinde belirtilen genel bir temsilci kullanılarak çağrılır.

[!code-csharp[GenericMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#1)]
[!code-vb[GenericMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Emit.MethodBuilder>
- [Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama](how-to-define-a-generic-type-with-reflection-emit.md)
