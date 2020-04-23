---
title: 'Nasıl yapılır: Yansıma Yayma ile Genel Yöntem Tanımlama'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- generics [.NET Framework], reflection emit
- reflection emit, generic methods
- generics [.NET Framework], dynamic types
ms.assetid: 93892fa4-90b3-4ec4-b147-4bec9880de2b
ms.openlocfilehash: d16f6728b01583fe3ffb8d892522f3892444c537
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73130169"
---
# <a name="how-to-define-a-generic-method-with-reflection-emit"></a>Nasıl yapılır: Yansıma Yayma ile Genel Yöntem Tanımlama

İlk yordam, iki tür parametresiyle basit bir genel yöntemin nasıl oluşturulacağını ve sınıf kısıtlamalarının, arabirim kısıtlamalarının ve özel kısıtlamaların tür parametrelerine nasıl uygulanacağını gösterir.

İkinci yordam, Yöntem gövdesinin nasıl yayılacağını ve genel türlerin örneklerini oluşturmak ve yöntemlerini çağırmak için genel yöntemin tür parametrelerinin nasıl kullanılacağını gösterir.

Üçüncü yordam genel yöntemin nasıl çağıralınacağını gösterir.

> [!IMPORTANT]
> Yalnızca genel bir türe ait olduğundan ve bu türün tür parametrelerini kullandığından bir yöntem genel değildir. Bir yöntem, yalnızca kendi tür parametresi listesine sahipse geneldir. Genel bir yöntem, bu örnekte olduğu gibi genel olmayan bir tür üzerinde bulunabilir. Genel türde genel olmayan bir metoda örnek için bkz. [nasıl yapılır: yansıma yayma Ile genel tür tanımlama](how-to-define-a-generic-type-with-reflection-emit.md).

### <a name="to-define-a-generic-method"></a>Genel bir yöntemi tanımlamak için

1. Başlamadan önce, üst düzey bir dil kullanılarak yazıldığında genel yöntemin nasıl göründüğünü bakmak yararlı olur. Aşağıdaki kod, genel yöntemi çağırmak için kod ile birlikte bu konunun örnek koduna dahildir. `TInput` Yöntemi iki tür parametresine sahiptir ve `TOutput`ikinci öğesinin bir başvuru türü (`class`) olması gereken, parametresiz bir oluşturucuya (`new`) sahip olması ve uygulaması `ICollection(Of TInput)` gerekir (`ICollection<TInput>` C# ' de). Bu arabirim kısıtlaması, yönteminin, <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemin oluşturduğu `TOutput` koleksiyona öğe eklemek için kullanılmasını sağlar. Yönteminde, bir dizisi olan bir biçimsel `input`parametre vardır `TInput`. Yöntemi, türünde `TOutput` bir koleksiyon oluşturur ve öğelerini `input` koleksiyona kopyalar.

    [!code-csharp[GenericMethodHowTo#20](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#20)]
    [!code-vb[GenericMethodHowTo#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#20)]

2. Genel yöntemin ait olduğu türü içeren bir dinamik derleme ve dinamik modül tanımlayın. Bu durumda, derleme yalnızca bir modüle `DemoMethodBuilder1`sahiptir ve modül adı derleme adının yanı sıra bir uzantıyla aynıdır. Bu örnekte, derleme diske kaydedilir ve de yürütülür, bu nedenle <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> belirtilir. DemoMethodBuilder1. dll ' yi incelemek ve adım 1 ' de gösterilen metodun Microsoft ara dili (MSIL) ile karşılaştırmak için [ıldadsm. exe ' yi (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.

    [!code-csharp[GenericMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#2)]
    [!code-vb[GenericMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#2)]

3. Genel yöntemin ait olduğu türü tanımlayın. Türün genel olması gerekmez. Genel bir yöntem genel ya da genel olmayan bir türe ait olabilir. Bu örnekte, tür bir sınıftır, genel değildir ve adlandırılır `DemoType`.

    [!code-csharp[GenericMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#3)]
    [!code-vb[GenericMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#3)]

4. Genel yöntemi tanımlayın. Genel yöntemin biçimsel parametrelerinin türleri genel yöntemin genel tür parametreleriyle belirtilmişse, yöntemi tanımlamak için <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%28System.String%2CSystem.Reflection.MethodAttributes%29> yöntem aşırı yüklemesini kullanın. Metodun genel tür parametreleri henüz tanımlı değil, bu nedenle, çağrısındaki metodun biçimsel parametrelerinin türlerini belirtemezsiniz <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%2A>. Bu örnekte, yöntemi olarak adlandırılmıştır `Factory`. Yöntemi geneldir ve `static` (`Shared` Visual Basic).

    [!code-csharp[GenericMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#4)]
    [!code-vb[GenericMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#4)]

5. Yöntemine parametre adlarını içeren bir dize `DemoMethod` dizisini geçirerek genel tür parametrelerini tanımlayın. <xref:System.Reflection.Emit.MethodBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> Bu, yöntemi genel bir yöntem yapar. Aşağıdaki kod, tür `Factory` parametreleri `TInput` ve `TOutput`olan genel bir yöntem oluşturur. Kodu daha kolay okunabilir hale getirmek için, bu adlara sahip değişkenler, iki tür parametresini temsil <xref:System.Reflection.Emit.GenericTypeParameterBuilder> eden nesneleri tutmak üzere oluşturulur.

    [!code-csharp[GenericMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#5)]
    [!code-vb[GenericMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#5)]

6. İsteğe bağlı olarak tür parametrelerine özel kısıtlamalar ekleyin. Özel kısıtlamalar <xref:System.Reflection.Emit.GenericTypeParameterBuilder.SetGenericParameterAttributes%2A> yöntemi kullanılarak eklenir. Bu örnekte, `TOutput` bir başvuru türü ve parametresiz bir oluşturucuya sahip olmak için kısıtlanmıştır.

    [!code-csharp[GenericMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#6)]
    [!code-vb[GenericMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#6)]

7. İsteğe bağlı olarak tür parametrelerine sınıf ve arabirim kısıtlamaları ekleyin. Bu örnekte, tür parametresi `TOutput` `ICollection(Of TInput)` (`ICollection<TInput>` C# ' de) arabirimini uygulayan türlerle sınırlıdır. Bu yöntem, <xref:System.Collections.Generic.ICollection%601.Add%2A> yöntemin öğe eklemek için kullanılmasını sağlar.

    [!code-csharp[GenericMethodHowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#7)]
    [!code-vb[GenericMethodHowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#7)]

8. Yöntemini kullanarak <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> yönteminin biçimsel parametrelerini tanımlayın. Bu örnekte, `Factory` yönteminin bir dizisi olan bir parametresi vardır `TInput`. Bu tür, <xref:System.Reflection.Emit.GenericTypeParameterBuilder> öğesini temsil `TInput`eden üzerinde <xref:System.Type.MakeArrayType%2A> yöntemi çağırarak oluşturulur. Bağımsız değişkeni <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> bir <xref:System.Type> nesne dizisidir.

    [!code-csharp[GenericMethodHowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#8)]
    [!code-vb[GenericMethodHowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#8)]

9. Yöntemini kullanarak <xref:System.Reflection.Emit.MethodBuilder.SetReturnType%2A> yöntemi için dönüş türünü tanımlayın. Bu örnekte, bir örneği `TOutput` döndürülür.

    [!code-csharp[GenericMethodHowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#9)]
    [!code-vb[GenericMethodHowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#9)]

10. Yöntemini kullanarak <xref:System.Reflection.Emit.ILGenerator>Yöntem gövdesini yay. Ayrıntılar için bkz. Yöntem gövdesini yayma için eşlik eden yordam.

    > [!IMPORTANT]
    > Çağrıları genel türdeki yöntemlere yaydığınızda ve bu türlerin tür bağımsız değişkenleri genel yöntemin tür parametreleridir, yöntemlerin oluşturulmuş biçimlerini almak için `static` <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29> <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> <xref:System.Reflection.Emit.TypeBuilder.GetField%28System.Type%2CSystem.Reflection.FieldInfo%29> <xref:System.Reflection.Emit.TypeBuilder> sınıfının, ve Yöntem yüklerini kullanmanız gerekir. Yöntem gövdesini yayma yordamı bunu gösterir.

11. Yöntemini içeren türü doldurun ve derlemeyi kaydedin. Genel yöntemi çağırmak için eşlik eden yordam, tamamlanmış yöntemi çağırmak için iki yol gösterir.

    [!code-csharp[GenericMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#14)]
    [!code-vb[GenericMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#14)]

<a name="procedureSection1"></a>

### <a name="to-emit-the-method-body"></a>Yöntem gövdesini yayma

1. Bir kod Oluşturucu alın ve yerel değişkenleri ve etiketleri bildirin. <xref:System.Reflection.Emit.ILGenerator.DeclareLocal%2A> Yöntemi yerel değişkenleri bildirmek için kullanılır. `Factory` Yöntemi dört `retVal` yerel değişkene sahiptir: yöntemi tarafından döndürülen yeni `TOutput` ' yi `ic` `TOutput` tutmak, `ICollection(Of TInput)` `ICollection<TInput>` `input` `TInput` nesne giriş dizisini tutmak ve `index` dizi boyunca yinelemek için, yöntemini (C# ' ta) tutmak için. Bu yöntemde, bir, bir diğeri (`enterLoop`) ve bir diğeri (`loopAgain`), <xref:System.Reflection.Emit.ILGenerator.DefineLabel%2A> yöntemi kullanılarak tanımlanan döngü () için iki etiket vardır.

    İlk şey yöntemi Opcode kullanarak <xref:System.Reflection.Emit.OpCodes.Ldarg_0> bağımsız değişkenini yüklemek ve Opcode kullanarak `input` <xref:System.Reflection.Emit.OpCodes.Stloc_S> yerel değişkende depolamak.

    [!code-csharp[GenericMethodHowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#10)]
    [!code-vb[GenericMethodHowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#10)]

2. Yönteminin genel yöntem aşırı yüklemesini kullanarak bir `TOutput`örneğini oluşturmak için kodu yay. <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> Bu aşırı yüklemeyi kullanmak, belirtilen türün parametresiz bir oluşturucuya sahip olmasını gerektirir ve bu kısıtlamayı öğesine `TOutput`ekleme nedenidir. Öğesine `TOutput` <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>geçirerek oluşturulan genel yöntemi oluşturun. Yöntemi çağırmak için kodu gönderdikten sonra, kullanarak kodu yerel değişkende `retVal` depolayın<xref:System.Reflection.Emit.OpCodes.Stloc_S>

    [!code-csharp[GenericMethodHowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#11)]
    [!code-vb[GenericMethodHowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#11)]

3. Yeni `TOutput` nesneyi atamak `ICollection(Of TInput)` ve yerel değişkende `ic`saklamak için kodu yay.

    [!code-csharp[GenericMethodHowTo#31](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#31)]
    [!code-vb[GenericMethodHowTo#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#31)]

4. <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> Yöntemi <xref:System.Reflection.MethodInfo> temsil edin. Yöntemi bir `ICollection(Of TInput)` (`ICollection<TInput>` C# ' ta) üzerinde davranıyor, bu nedenle, bu oluşturulmuş türe özgü `Add` yöntemi almak için gereklidir. İle oluşturulmuş bir tür <xref:System.Type.GetMethod%2A> üzerinde desteklenmediğinden, bunu <xref:System.Reflection.MethodInfo> doğrudan ' `icollOfTInput` <xref:System.Type.GetMethod%2A> den almak için yöntemini kullanamazsınız <xref:System.Reflection.Emit.GenericTypeParameterBuilder>. Bunun yerine, <xref:System.Type.GetMethod%2A> <xref:System.Collections.Generic.ICollection%601> genel `icoll`arabirim için genel tür tanımını içeren öğesini çağırın. Daha sonra, <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> `static` <xref:System.Reflection.MethodInfo> oluşturulan tür için oluşturmak için yöntemini kullanın. Aşağıdaki kod bunu gösterir.

    [!code-csharp[GenericMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#12)]
    [!code-vb[GenericMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#12)]

5. 32 bitlik bir tamsayı yükleyerek `index` ve bunu değişkende depolayarak değişkeni başlatmak için kodu yay. Kodu Dala Dala yay `enterLoop`. Bu etiket, döngünün içinde olduğundan henüz işaretlenmedi. Döngü kodu bir sonraki adımda yayılır.

    [!code-csharp[GenericMethodHowTo#32](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#32)]
    [!code-vb[GenericMethodHowTo#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#32)]

6. Döngü için kod yay. İlk adım, <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> `loopAgain` etiketiyle çağırarak döngünün en üstünü işaretlemenize neden olur. Etiketi kullanan dal deyimleri artık koddaki bu noktaya dallandıracaktır. Bir sonraki adım, `TOutput` nesnesini yığına itmeniz, nesneye dönüştürmelisiniz `ICollection(Of TInput)`. Hemen gerekli değildir, ancak `Add` yöntemini çağırmak için konumunda olması gerekir. Giriş dizisi bir sonraki yığına gönderilir ve sonra dizideki geçerli dizini içeren `index` değişken. <xref:System.Reflection.Emit.OpCodes.Ldelem> Opcode dizin ve diziyi yığın dışına çıkarır ve dizinli dizi öğesini yığına gönderir. Yığın artık <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemi çağrısı için hazırdır. Bu, koleksiyonu ve yeni öğeyi yığının dışına çıkarır ve öğeyi koleksiyona ekler.

    Döngüdeki kodun geri kalanı dizini arttırır ve döngünün tamamlanıp bitmediğini görmek için sınar: Dizin ve 32 bitlik bir tamsayı 1 yığına gönderilir ve yığında toplamı bırakır; Toplam, içinde `index`depolanır. <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A>Bu noktayı döngünün giriş noktası olarak ayarlamak için çağırılır. Dizin yeniden yüklendi. Giriş dizisi yığına gönderilir ve <xref:System.Reflection.Emit.OpCodes.Ldlen> uzunluğunu almak için yayılır. Dizin ve uzunluk artık yığında bulunur ve <xref:System.Reflection.Emit.OpCodes.Clt> bunları karşılaştırmaya yönelik olarak yayılır. Dizin uzunluktan küçükse, <xref:System.Reflection.Emit.OpCodes.Brtrue_S> döngünün başlangıcına geri dallanma.

    [!code-csharp[GenericMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#13)]
    [!code-vb[GenericMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#13)]

7. `TOutput` Nesneyi yığına göndermek ve yönteminden döndürmek için kodu yay. Yerel değişkenler `retVal` ve `ic` her ikisi de yeni `TOutput`başvuruları içerir; `ic` yalnızca <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemine erişmek için kullanılır.

    [!code-csharp[GenericMethodHowTo#33](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#33)]
    [!code-vb[GenericMethodHowTo#33](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#33)]

<a name="procedureSection2"></a>

### <a name="to-invoke-the-generic-method"></a>Genel yöntemi çağırmak için

1. `Factory`genel bir yöntem tanımıdır. Çağırmak için, türleri genel tür parametrelerine atamanız gerekir. Bunu yapmak <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> için yöntemini kullanın. Aşağıdaki kod, <xref:System.String> için `TInput` `List(Of String)` `List<string>` `TOutput`ve için (C# ' de) belirterek oluşturulmuş bir genel yöntem oluşturur ve yönteminin bir dize gösterimini görüntüler.

    [!code-csharp[GenericMethodHowTo#21](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#21)]
    [!code-vb[GenericMethodHowTo#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#21)]

2. Geç bağlantılı yöntemi çağırmak için <xref:System.Reflection.MethodBase.Invoke%2A> yöntemini kullanın. Aşağıdaki kod, tek öğesi bir dize <xref:System.Object>dizisi olarak içeren öğesinin bir dizisini oluşturur ve bunu genel yöntem için bağımsız değişken listesi olarak geçirir. Yöntemi olduğundan, ilk <xref:System.Reflection.MethodBase.Invoke%2A> parametresi null bir başvurudur `static`. Dönüş değeri öğesine `List(Of String)`ve ilk öğesi görüntülenir.

    [!code-csharp[GenericMethodHowTo#22](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#22)]
    [!code-vb[GenericMethodHowTo#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#22)]

3. Bir temsilciyi kullanarak yöntemi çağırmak için, oluşturulan genel yöntemin imzasıyla eşleşen bir temsilciye sahip olmanız gerekir. Bunu yapmanın kolay bir yolu, genel bir temsilci oluşturmaktır. Aşağıdaki kod, <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType> yöntem aşırı yüklemesini kullanarak örnek kodda tanımlanan `D` genel temsilcinin bir örneğini oluşturur ve temsilciyi çağırır. Temsilciler, geç bağlantılı çağrılara göre daha iyi gerçekleştirir.

    [!code-csharp[GenericMethodHowTo#23](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#23)]
    [!code-vb[GenericMethodHowTo#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#23)]

4. Yayınlanan Yöntem, kaydedilen derlemeye başvuran bir programdan de çağrılabilir.

## <a name="example"></a>Örnek

Aşağıdaki kod örneği, genel bir yöntemi olan genel olmayan `DemoType`bir tür oluşturur `Factory`. Bu yöntemin, `TInput` bir giriş türü belirtmek ve `TOutput` bir çıkış türü belirtmek için iki genel tür parametresi vardır. `TOutput` Tür parametresi, `ICollection<TInput>` (`ICollection(Of TInput)` Visual Basic olarak), başvuru türü ve parametresiz bir oluşturucuya sahip olmak için sınırlandırılır.

Yönteminde bir dizisi olan bir biçimsel parametre vardır `TInput`. Yöntemi, giriş dizisinin tüm öğelerini `TOutput` içeren bir örneğini döndürür. `TOutput`<xref:System.Collections.Generic.ICollection%601> genel arabirimi uygulayan herhangi bir genel koleksiyon türü olabilir.

Kod yürütüldüğünde, dinamik derleme DemoGenericMethod1. dll olarak kaydedilir ve [ıldadsm. exe (IL Disassembler)](../tools/ildasm-exe-il-disassembler.md)kullanılarak incelenebilir.

> [!NOTE]
> Kodu nasıl yayılacağınızı öğrenmek, oluşturmaya çalıştığınız görevi gerçekleştiren bir Visual Basic, C# veya Visual C++ programını yazmak ve derleyici tarafından üretilen MSIL 'yi incelemek için ayrıştırıcı 'yi kullanmak için iyi bir yoldur.

Kod örneği, yayılan yönteme denk gelen kaynak kodunu içerir. Yayınlanan Yöntem, geç ve ayrıca kod örneğinde belirtilen genel bir temsilci kullanılarak çağrılır.

[!code-csharp[GenericMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#1)]
[!code-vb[GenericMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#1)]

## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Emit.MethodBuilder>
- [Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama](how-to-define-a-generic-type-with-reflection-emit.md)
