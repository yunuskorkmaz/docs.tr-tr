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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a16f51408de5ed7b2a0a7d45af81113fe8c7b386
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928289"
---
# <a name="how-to-define-a-generic-method-with-reflection-emit"></a>Nasıl yapılır: Yansıma Yayma ile Genel Yöntem Tanımlama
İlk yordam, iki tür parametresiyle basit bir genel yöntemin nasıl oluşturulacağını ve sınıf kısıtlamalarının, arabirim kısıtlamalarının ve özel kısıtlamaların tür parametrelerine nasıl uygulanacağını gösterir.  
  
 İkinci yordam, Yöntem gövdesinin nasıl yayılacağını ve genel türlerin örneklerini oluşturmak ve yöntemlerini çağırmak için genel yöntemin tür parametrelerinin nasıl kullanılacağını gösterir.  
  
 Üçüncü yordam genel yöntemin nasıl çağıralınacağını gösterir.  
  
> [!IMPORTANT]
> Yalnızca genel bir türe ait olduğundan ve bu türün tür parametrelerini kullandığından bir yöntem genel değildir. Bir yöntem, yalnızca kendi tür parametresi listesine sahipse geneldir. Genel bir yöntem, bu örnekte olduğu gibi genel olmayan bir tür üzerinde bulunabilir. Genel türde genel olmayan bir metoda örnek için bkz [. nasıl yapılır: Yansıma yayma](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)Ile genel bir tür tanımlayın.  
  
### <a name="to-define-a-generic-method"></a>Genel bir yöntemi tanımlamak için  
  
1. Başlamadan önce, üst düzey bir dil kullanılarak yazıldığında genel yöntemin nasıl göründüğünü bakmak yararlı olur. Aşağıdaki kod, genel yöntemi çağırmak için kod ile birlikte bu konunun örnek koduna dahildir. `TInput` Yöntemi iki tür parametresine sahiptir ve `TOutput`ikincisinin bir başvuru türü (`class`) olması gerekir, parametresiz bir oluşturucuya (`new`) sahip olmalı ve uygulaması `ICollection(Of TInput)` gerekir (`ICollection<TInput>` C#). Bu arabirim kısıtlaması, yönteminin, <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemin oluşturduğu `TOutput` koleksiyona öğe eklemek için kullanılmasını sağlar. Yönteminde, bir `TInput`dizisi olan bir biçimsel `input`parametre vardır. Yöntemi, türünde `TOutput` bir koleksiyon oluşturur ve `input` öğelerini koleksiyona kopyalar.  
  
     [!code-csharp[GenericMethodHowTo#20](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#20)]
     [!code-vb[GenericMethodHowTo#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#20)]  
  
2. Genel yöntemin ait olduğu türü içeren bir dinamik derleme ve dinamik modül tanımlayın. Bu durumda, derleme yalnızca bir modüle `DemoMethodBuilder1`sahiptir ve modül adı derleme adının yanı sıra bir uzantıyla aynıdır. Bu örnekte, derleme diske kaydedilir ve de yürütülür, bu nedenle <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> belirtilir. DemoMethodBuilder1. dll ' yi incelemek ve adım 1 ' de gösterilen metodun Microsoft ara dili (MSIL) ile karşılaştırmak için [ıldadsm. exe ' yi (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) kullanabilirsiniz.  
  
     [!code-csharp[GenericMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#2)]
     [!code-vb[GenericMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#2)]  
  
3. Genel yöntemin ait olduğu türü tanımlayın. Türün genel olması gerekmez. Genel bir yöntem genel ya da genel olmayan bir türe ait olabilir. Bu örnekte, tür bir sınıftır, genel değildir ve adlandırılır `DemoType`.  
  
     [!code-csharp[GenericMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#3)]
     [!code-vb[GenericMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#3)]  
  
4. Genel yöntemi tanımlayın. Genel yöntemin biçimsel parametrelerinin türleri genel yöntemin genel tür parametreleriyle belirtilmişse, yöntemi tanımlamak için <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%28System.String%2CSystem.Reflection.MethodAttributes%29> yöntem aşırı yüklemesini kullanın. Metodun genel tür parametreleri henüz tanımlı değil, bu nedenle, çağrısındaki <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%2A>metodun biçimsel parametrelerinin türlerini belirtemezsiniz. Bu örnekte, yöntemi olarak adlandırılmıştır `Factory`. Yöntemi geneldir ve `static` (`Shared` Visual Basic).  
  
     [!code-csharp[GenericMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#4)]
     [!code-vb[GenericMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#4)]  
  
5. Yöntemine<xref:System.Reflection.Emit.MethodBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> parametre adlarını içeren bir dize `DemoMethod` dizisini geçirerek genel tür parametrelerini tanımlayın. Bu, yöntemi genel bir yöntem yapar. Aşağıdaki kod, tür `Factory` parametreleri `TInput` ve `TOutput`olan genel bir yöntem oluşturur. Kodu daha kolay okunabilir hale getirmek için, bu adlara sahip değişkenler, iki tür parametresini temsil <xref:System.Reflection.Emit.GenericTypeParameterBuilder> eden nesneleri tutmak üzere oluşturulur.  
  
     [!code-csharp[GenericMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#5)]
     [!code-vb[GenericMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#5)]  
  
6. İsteğe bağlı olarak tür parametrelerine özel kısıtlamalar ekleyin. Özel kısıtlamalar <xref:System.Reflection.Emit.GenericTypeParameterBuilder.SetGenericParameterAttributes%2A> yöntemi kullanılarak eklenir. Bu örnekte, `TOutput` bir başvuru türü ve parametresiz bir oluşturucuya sahip olmak için kısıtlanmıştır.  
  
     [!code-csharp[GenericMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#6)]
     [!code-vb[GenericMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#6)]  
  
7. İsteğe bağlı olarak tür parametrelerine sınıf ve arabirim kısıtlamaları ekleyin. Bu `TOutput` örnekte, tür parametresi `ICollection(Of TInput)` (`ICollection<TInput>` ın C#) arabirimini uygulayan türlerle sınırlıdır. Bu yöntem, <xref:System.Collections.Generic.ICollection%601.Add%2A> yöntemin öğe eklemek için kullanılmasını sağlar.  
  
     [!code-csharp[GenericMethodHowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#7)]
     [!code-vb[GenericMethodHowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#7)]  
  
8. Yöntemini kullanarak <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> yönteminin biçimsel parametrelerini tanımlayın. Bu örnekte, `Factory` yönteminin bir `TInput`dizisi olan bir parametresi vardır. Bu tür, <xref:System.Type.MakeArrayType%2A> <xref:System.Reflection.Emit.GenericTypeParameterBuilder> öğesini temsil `TInput`eden üzerinde yöntemi çağırarak oluşturulur. Bağımsız değişkeni <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> bir <xref:System.Type> nesne dizisidir.  
  
     [!code-csharp[GenericMethodHowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#8)]
     [!code-vb[GenericMethodHowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#8)]  
  
9. Yöntemini kullanarak <xref:System.Reflection.Emit.MethodBuilder.SetReturnType%2A> yöntemi için dönüş türünü tanımlayın. Bu örnekte, bir örneği `TOutput` döndürülür.  
  
     [!code-csharp[GenericMethodHowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#9)]
     [!code-vb[GenericMethodHowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#9)]  
  
10. Yöntemini kullanarak <xref:System.Reflection.Emit.ILGenerator>Yöntem gövdesini yay. Ayrıntılar için bkz. Yöntem gövdesini yayma için eşlik eden yordam.  
  
    > [!IMPORTANT]
    >  Çağrıları genel türdeki yöntemlere yaydığınızda ve bu türlerin tür bağımsız değişkenleri `static`genel yöntemin tür parametreleri ise, <xref:System.Reflection.Emit.TypeBuilder> sınıfının <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29>, <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29>ve <xref:System.Reflection.Emit.TypeBuilder.GetField%28System.Type%2CSystem.Reflection.FieldInfo%29> yöntem aşırı yüklerini kullanarak yöntemlerin oluşturulmuş biçimlerini alın. Yöntem gövdesini yayma yordamı bunu gösterir.  
  
11. Yöntemini içeren türü doldurun ve derlemeyi kaydedin. Genel yöntemi çağırmak için eşlik eden yordam, tamamlanmış yöntemi çağırmak için iki yol gösterir.  
  
     [!code-csharp[GenericMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#14)]
     [!code-vb[GenericMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#14)]  
  
<a name="procedureSection1"></a>   
### <a name="to-emit-the-method-body"></a>Yöntem gövdesini yayma  
  
1. Bir kod Oluşturucu alın ve yerel değişkenleri ve etiketleri bildirin. <xref:System.Reflection.Emit.ILGenerator.DeclareLocal%2A> Yöntemi yerel değişkenleri bildirmek için kullanılır. `ic` `TOutput` `retVal` `ICollection<TInput>`Yöntemindört yerel değişkeni vardır: yöntemi`TOutput`tarafındandöndürülen yeni ' yi tutmak için, C# (içinde`ICollection(Of TInput)`), `Factory` `input`nesnelerin giriş dizisini `index` tutmak ve dizi boyunca yinelemek için. `TInput` Bu yöntemde, bir, bir diğeri`enterLoop`() ve bir diğeri (`loopAgain`), <xref:System.Reflection.Emit.ILGenerator.DefineLabel%2A> yöntemi kullanılarak tanımlanan döngü () için iki etiket vardır.  
  
     İlk şey yöntemi Opcode kullanarak <xref:System.Reflection.Emit.OpCodes.Ldarg_0> bağımsız değişkenini yüklemek ve Opcode kullanarak <xref:System.Reflection.Emit.OpCodes.Stloc_S> yerel değişkende `input` depolamak.  
  
     [!code-csharp[GenericMethodHowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#10)]
     [!code-vb[GenericMethodHowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#10)]  
  
2. <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> Yönteminin genel yöntem aşırı yüklemesini kullanarak bir `TOutput`örneğini oluşturmak için kodu yay. Bu aşırı yüklemeyi kullanmak, belirtilen türün parametresiz bir oluşturucuya sahip olmasını gerektirir ve bu kısıtlamayı öğesine `TOutput`ekleme nedenidir. `TOutput` Öğesine<xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>geçirerek oluşturulan genel yöntemi oluşturun. Yöntemi çağırmak için kodu gönderdikten sonra, kullanarak kodu yerel değişkende `retVal` depolayın<xref:System.Reflection.Emit.OpCodes.Stloc_S>  
  
     [!code-csharp[GenericMethodHowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#11)]
     [!code-vb[GenericMethodHowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#11)]  
  
3. Yeni `TOutput` nesneyi atamak `ICollection(Of TInput)` ve yerel değişkende `ic`saklamak için kodu yay.  
  
     [!code-csharp[GenericMethodHowTo#31](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#31)]
     [!code-vb[GenericMethodHowTo#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#31)]  
  
4. Yöntemi<xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType>temsiledin. <xref:System.Reflection.MethodInfo> Yöntemi bir `ICollection(Of TInput)` (`ICollection<TInput>` ' de C#) üzerinde davranıyor, bu `Add` nedenle, söz konusu oluşturulmuş türe özgü yöntemi almak gereklidir. İle <xref:System.Type.GetMethod%2A> <xref:System.Reflection.MethodInfo> `icollOfTInput` oluşturulmuşbir<xref:System.Type.GetMethod%2A> tür üzerinde desteklenmediğinden, bunu doğrudan ' den almak için yöntemini kullanamazsınız. <xref:System.Reflection.Emit.GenericTypeParameterBuilder> Bunun yerine, <xref:System.Type.GetMethod%2A> <xref:System.Collections.Generic.ICollection%601> genel `icoll`arabirim için genel tür tanımını içeren öğesini çağırın. Daha sonra, <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> `static` oluşturulan<xref:System.Reflection.MethodInfo> tür için oluşturmak için yöntemini kullanın. Aşağıdaki kod bunu gösterir.  
  
     [!code-csharp[GenericMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#12)]
     [!code-vb[GenericMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#12)]  
  
5. 32 bitlik bir tamsayı yükleyerek `index` ve bunu değişkende depolayarak değişkeni başlatmak için kodu yay. Kodu Dala Dala `enterLoop`yay. Bu etiket, döngünün içinde olduğundan henüz işaretlenmedi. Döngü kodu bir sonraki adımda yayılır.  
  
     [!code-csharp[GenericMethodHowTo#32](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#32)]
     [!code-vb[GenericMethodHowTo#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#32)]  
  
6. Döngü için kod yay. İlk adım, <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> `loopAgain` etiketiyle çağırarak döngünün en üstünü işaretlemenize neden olur. Etiketi kullanan dal deyimleri artık koddaki bu noktaya dallandıracaktır. Bir sonraki adım, `TOutput` nesnesini yığına itmeniz, nesneye `ICollection(Of TInput)`dönüştürmelisiniz. Hemen gerekli değildir, ancak `Add` yöntemini çağırmak için konumunda olması gerekir. Giriş dizisi bir sonraki yığına gönderilir ve sonra `index` dizideki geçerli dizini içeren değişken. <xref:System.Reflection.Emit.OpCodes.Ldelem> Opcode dizin ve diziyi yığın dışına çıkarır ve dizinli dizi öğesini yığına gönderir. Yığın artık <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemi çağrısı için hazırdır. Bu, koleksiyonu ve yeni öğeyi yığının dışına çıkarır ve öğeyi koleksiyona ekler.  
  
     Döngüdeki kodun geri kalanı dizini arttırır ve döngünün tamamlanıp bitmediğini görmek için sınar: Dizin ve 32 bitlik bir tamsayı 1 yığına gönderilir ve yığında toplamı bırakarak eklenir; Toplam, içinde `index`depolanır. <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A>Bu noktayı döngünün giriş noktası olarak ayarlamak için çağırılır. Dizin yeniden yüklendi. Giriş dizisi yığına gönderilir ve <xref:System.Reflection.Emit.OpCodes.Ldlen> uzunluğunu almak için yayılır. Dizin ve uzunluk artık yığında bulunur ve <xref:System.Reflection.Emit.OpCodes.Clt> bunları karşılaştırmaya yönelik olarak yayılır. Dizin uzunluktan küçükse, <xref:System.Reflection.Emit.OpCodes.Brtrue_S> döngünün başlangıcına geri dallanma.  
  
     [!code-csharp[GenericMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#13)]
     [!code-vb[GenericMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#13)]  
  
7. `TOutput` Nesneyi yığına göndermek ve yönteminden döndürmek için kodu yay. Yerel değişkenler `retVal` ve `ic` her ikisi de yeni `TOutput`başvuruları içerir; `ic` yalnızca yöntemine<xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> erişmek için kullanılır.  
  
     [!code-csharp[GenericMethodHowTo#33](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#33)]
     [!code-vb[GenericMethodHowTo#33](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#33)]  
  
<a name="procedureSection2"></a>   
### <a name="to-invoke-the-generic-method"></a>Genel yöntemi çağırmak için  
  
1. `Factory`genel bir yöntem tanımıdır. Çağırmak için, türleri genel tür parametrelerine atamanız gerekir. Bunu yapmak için yöntemini kullanın. <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> Aşağıdaki kod <xref:System.String> , için `TInput` `List<string>` C#ve için ve `List(Of String)` (içinde) için belirterek oluşturulmuş bir genel yöntem oluşturur ve yönteminin bir dize gösterimini görüntüler. `TOutput`  
  
     [!code-csharp[GenericMethodHowTo#21](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#21)]
     [!code-vb[GenericMethodHowTo#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#21)]  
  
2. Geç bağlantılı yöntemi çağırmak için <xref:System.Reflection.MethodBase.Invoke%2A> yöntemini kullanın. Aşağıdaki kod, tek öğesi bir dize <xref:System.Object>dizisi olarak içeren öğesinin bir dizisini oluşturur ve bunu genel yöntem için bağımsız değişken listesi olarak geçirir. Yöntemi olduğundan, ilk <xref:System.Reflection.MethodBase.Invoke%2A> parametresi null bir başvurudur. `static` Dönüş değeri öğesine `List(Of String)`ve ilk öğesi görüntülenir.  
  
     [!code-csharp[GenericMethodHowTo#22](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#22)]
     [!code-vb[GenericMethodHowTo#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#22)]  
  
3. Bir temsilciyi kullanarak yöntemi çağırmak için, oluşturulan genel yöntemin imzasıyla eşleşen bir temsilciye sahip olmanız gerekir. Bunu yapmanın kolay bir yolu, genel bir temsilci oluşturmaktır. Aşağıdaki kod, <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType> yöntem aşırı yüklemesini kullanarak örnek kodda tanımlanan `D` genel temsilcinin bir örneğini oluşturur ve temsilciyi çağırır. Temsilciler, geç bağlantılı çağrılara göre daha iyi gerçekleştirir.  
  
     [!code-csharp[GenericMethodHowTo#23](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#23)]
     [!code-vb[GenericMethodHowTo#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#23)]  
  
4. Yayınlanan Yöntem, kaydedilen derlemeye başvuran bir programdan de çağrılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği, genel bir `DemoType` `Factory`yöntemi olan genel olmayan bir tür oluşturur. Bu yöntemin, `TInput` bir giriş türü belirtmek ve `TOutput` bir çıkış türü belirtmek için iki genel tür parametresi vardır. Tür parametresi, `ICollection<TInput>` (`ICollection(Of TInput)` Visual Basic olarak), başvuru türü ve parametresiz bir oluşturucuya sahip olmak için sınırlandırılır. `TOutput`  
  
 Yönteminde bir dizisi `TInput`olan bir biçimsel parametre vardır. Yöntemi, giriş dizisinin tüm öğelerini `TOutput` içeren bir örneğini döndürür. `TOutput`<xref:System.Collections.Generic.ICollection%601> genel arabirimi uygulayan herhangi bir genel koleksiyon türü olabilir.  
  
 Kod yürütüldüğünde, dinamik derleme DemoGenericMethod1. dll olarak kaydedilir ve [ıldadsm. exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)kullanılarak incelenebilir.  
  
> [!NOTE]
> Kodu nasıl yayılacağınızı öğrenmek, oluşturmaya çalıştığınız görevi gerçekleştiren Visual Basic, C#ya da görsel C++ programı yazmak ve derleyici tarafından üretilen MSIL 'yi incelemek için ayrıştırıcı 'yi kullanmak için iyi bir yoldur.  
  
 Kod örneği, yayılan yönteme denk gelen kaynak kodunu içerir. Yayınlanan Yöntem, geç ve ayrıca kod örneğinde belirtilen genel bir temsilci kullanılarak çağrılır.  
  
 [!code-csharp[GenericMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#1)]
 [!code-vb[GenericMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#1)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Emit.MethodBuilder>
- [Nasıl yapılır: Yansıma Yayma ile genel bir tür tanımlama](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)
