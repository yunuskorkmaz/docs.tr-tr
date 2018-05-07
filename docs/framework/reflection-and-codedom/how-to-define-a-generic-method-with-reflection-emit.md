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
ms.openlocfilehash: 49531945b073a909ba49b2b0865b96f9658fba50
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-a-generic-method-with-reflection-emit"></a>Nasıl yapılır: Yansıma Yayma ile Genel Yöntem Tanımlama
İlk yordam, iki tür parametreleri ile basit bir genel yöntem oluşturma ve tür parametreleri sınıf kısıtlamaları, arabirim kısıtlamaları ve özel kısıtlamalar uygulamak nasıl gösterir.  
  
 İkinci yordam yöntem gövdesi yaymak üzere nasıl ve genel yönteminin tür parametreleri genel türler örneklerini oluşturmak için ve bunların yöntemleri çağırmak için nasıl kullanılacağı gösterilmektedir.  
  
 Üçüncü yordam genel yöntemini çağırmak nasıl gösterir.  
  
> [!IMPORTANT]
>  Yalnızca genel bir tür ait ve bu tür tür parametreleri kullanan bir yöntem genel olmadığından. Yalnızca kendi türü parametre listesine varsa genel yöntemidir. Genel yöntem bu örnekte olduğu gibi bir nongeneric türü görünebilir. Genel bir tür nongeneric bir yöntem örneği için bkz: [nasıl yapılır: yansıma yayma ile genel tür tanımlama](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-method"></a>Genel bir yöntemi tanımlamak için  
  
1.  Başlamadan önce üst düzey bir dil kullanarak yazılırken genel yöntem nasıl göründüğü aramak yararlıdır. Aşağıdaki kod genel yöntemini çağırmak için kodu ile birlikte bu konu için örnek kod yer alır. İki tür parametreleri yöntemi sahip `TInput` ve `TOutput`, hangisinin bir başvuru türü olmalıdır ikinci (`class`), bir parametresiz oluşturucuya sahip olmalıdır (`new`) ve uygulamalıdır `ICollection(Of TInput)` (`ICollection<TInput>` C#). Bu arabirim kısıtlaması sağlar <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemi öğelerine eklemek için kullanılabilir `TOutput` yöntemi oluşturur koleksiyonu. Bir resmi parametresi yöntemi var `input`, bir dizi olduğu `TInput`. Yöntem türü bir koleksiyonunu oluşturur `TOutput` ve öğelerini kopyalar `input` koleksiyonuna.  
  
     [!code-csharp[GenericMethodHowTo#20](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#20)]
     [!code-vb[GenericMethodHowTo#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#20)]  
  
2.  Genel yöntem türü içeren bir dinamik modül ait ve bir dinamik derleme tanımlayın. Bu durumda, derleme adlı yalnızca bir modül sahip `DemoMethodBuilder1`, ve modül adına derleme adı artı bir uzantısı aynıdır. Bu örnekte, derleme diske kaydedilir ve aynı zamanda yürütülen, bunu <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> belirtilir. Kullanabileceğiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) DemoMethodBuilder1.dll inceleyin ve 1. adımda gösterilen yöntemi için Microsoft Ara dili (MSIL) karşılaştırın.  
  
     [!code-csharp[GenericMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#2)]
     [!code-vb[GenericMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#2)]  
  
3.  Genel yöntem ait türünü tanımlayın. Tür genel olmak zorunda değildir. Genel yöntem ya da bir genel veya nongeneric türüne ait olabilir. Bu örnekte, türü bir sınıf, genel değil ve adlı `DemoType`.  
  
     [!code-csharp[GenericMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#3)]
     [!code-vb[GenericMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#3)]  
  
4.  Genel yöntemi tanımlayın. Bir genel yöntemin resmi parametre türlerini genel yöntem genel tür parametresi tarafından belirtilen kullanırsanız <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%28System.String%2CSystem.Reflection.MethodAttributes%29> yöntemi aşırı yöntemi tanımlayın. Çağrısında yöntemin resmi parametre türlerini belirtemezsiniz yönteminin genel tür parametreleri henüz, tanımlanmamış <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%2A>. Bu örnekte, yöntem adlı `Factory`. Ortak bir yöntemdir ve `static` (`Shared` Visual Basic'te).  
  
     [!code-csharp[GenericMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#4)]
     [!code-vb[GenericMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#4)]  
  
5.  Genel tür parametreleri tanımla `DemoMethod` parametrelerinin adlarını içeren bir dizeler dizisi geçirerek <xref:System.Reflection.Emit.MethodBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> yöntemi. Bu yöntem genel bir yöntem sağlar. Aşağıdaki kod yapar `Factory` tür parametreleri ile genel yöntem `TInput` ve `TOutput`. Kod okunmasını kolaylaştırmak için bu adları değişkenlerle tutmak için oluşturulan <xref:System.Reflection.Emit.GenericTypeParameterBuilder> iki tür parametreleri temsil eden nesne.  
  
     [!code-csharp[GenericMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#5)]
     [!code-vb[GenericMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#5)]  
  
6.  İsteğe bağlı olarak özel kısıtlamalar tür parametreleri ekleyin. Özel kısıtlamalar kullanarak eklenir <xref:System.Reflection.Emit.GenericTypeParameterBuilder.SetGenericParameterAttributes%2A> yöntemi. Bu örnekte, `TOutput` bir başvuru türü olması ve parametresiz bir oluşturucuya sahip olması için sınırlı değildir.  
  
     [!code-csharp[GenericMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#6)]
     [!code-vb[GenericMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#6)]  
  
7.  İsteğe bağlı olarak sınıfı ve arabirim kısıtlamaları tür parametreleri ekleyin. Bu örnekte, tür parametresi `TOutput` uygulayan türler için kısıtlı `ICollection(Of TInput)` (`ICollection<TInput>` C#) arabirimi. Bu sağlar <xref:System.Collections.Generic.ICollection%601.Add%2A> yöntemi, öğeler eklemek için kullanılabilir.  
  
     [!code-csharp[GenericMethodHowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#7)]
     [!code-vb[GenericMethodHowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#7)]  
  
8.  Yöntemin resmi parametrelerini tanımlamak kullanarak <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> yöntemi. Bu örnekte, `Factory` yöntemi sahip bir parametre, bir dizi `TInput`. Bu tür çağrılarak oluşturulan <xref:System.Type.MakeArrayType%2A> yöntemi <xref:System.Reflection.Emit.GenericTypeParameterBuilder> temsil eden `TInput`. Bağımsız değişkeni <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> dizisidir <xref:System.Type> nesneleri.  
  
     [!code-csharp[GenericMethodHowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#8)]
     [!code-vb[GenericMethodHowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#8)]  
  
9. Yöntemin dönüş türünü tanımlayın kullanarak <xref:System.Reflection.Emit.MethodBuilder.SetReturnType%2A> yöntemi. Bu örnekte, bir örneğini `TOutput` döndürülür.  
  
     [!code-csharp[GenericMethodHowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#9)]
     [!code-vb[GenericMethodHowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#9)]  
  
10. Yöntem yayma gövde, kullanarak <xref:System.Reflection.Emit.ILGenerator>. Ayrıntılar için yöntem gövdesi yayma için eşlik eden yordamına bakın.  
  
    > [!IMPORTANT]
    >  Genel türler yöntemlerinin çağrıları yayma ve bu türlerin tür bağımsız değişkenleri genel yönteminin tür parametreleri olduğunda kullanmalısınız `static` <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29>, <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29>, ve <xref:System.Reflection.Emit.TypeBuilder.GetField%28System.Type%2CSystem.Reflection.FieldInfo%29> yöntemi aşırı yüklemeleri <xref:System.Reflection.Emit.TypeBuilder> için sınıfı oluşturulan form yöntemlerden birini alın. Yöntem gövdesi yayma eşlik eden yordamı bu gösterir.  
  
11. Contains yöntemi türü tamamlayın ve derlemeyi kaydedin. Genel yöntem çağırma eşlik eden yordamı tamamlanmış yöntemini çağırmak için iki yolunu gösterir.  
  
     [!code-csharp[GenericMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#14)]
     [!code-vb[GenericMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#14)]  
  
<a name="procedureSection1"></a>   
### <a name="to-emit-the-method-body"></a>Yöntem gövdesi yaymak üzere  
  
1.  Bir kod oluşturucuyu alın ve yerel değişkenleri ve etiketleri bildirin. <xref:System.Reflection.Emit.ILGenerator.DeclareLocal%2A> Yöntemi, yerel değişkenleri bildirmek için kullanılır. `Factory` Yöntemi olan dört yerel değişkenler: `retVal` yeni tutmak için `TOutput` yöntemi tarafından döndürülen `ic` tutmak için `TOutput` zaman onu atandığında `ICollection(Of TInput)` (`ICollection<TInput>` C#), `input` için Giriş dizisi tutun `TInput` nesneleri ve `index` dizi boyunca yinelemek için. Yöntemi de döngü girmek için iki etiket vardır (`enterLoop`) ve üst döngü için bir tane (`loopAgain`), tanımlı kullanarak <xref:System.Reflection.Emit.ILGenerator.DefineLabel%2A> yöntemi.  
  
     Yöntemi yapacağı ilk şey, bağımsız değişkeni kullanarak yüklemek için olan <xref:System.Reflection.Emit.OpCodes.Ldarg_0> opcode ve yerel değişkende saklamak için `input` kullanarak <xref:System.Reflection.Emit.OpCodes.Stloc_S> işlem kodu.  
  
     [!code-csharp[GenericMethodHowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#10)]
     [!code-vb[GenericMethodHowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#10)]  
  
2.  Örneği oluşturmak için kod yayma `TOutput`, genel yöntemi aşırı yüklemesini kullanarak <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> yöntemi. Bu aşırı yüklemeleri kullanarak belirtilen türün parametresiz bir oluşturucuya sahip olması gerektirir, kısıtlama eklemek için neden olduğu `TOutput`. Oluşturulan genel yöntem geçirerek oluşturma `TOutput` için <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>. Yöntemini çağırmak için kod yayma sonra yerel değişkende depolamak üzere kod yayma `retVal` kullanma <xref:System.Reflection.Emit.OpCodes.Stloc_S>  
  
     [!code-csharp[GenericMethodHowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#11)]
     [!code-vb[GenericMethodHowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#11)]  
  
3.  Yeni dönüştürmek için kod yayma `TOutput` nesnesini `ICollection(Of TInput)` ve yerel değişkende saklayın `ic`.  
  
     [!code-csharp[GenericMethodHowTo#31](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#31)]
     [!code-vb[GenericMethodHowTo#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#31)]  
  
4.  Alma bir <xref:System.Reflection.MethodInfo> temsil eden <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemi. Yöntem üzerinde çalışan bir `ICollection(Of TInput)` (`ICollection<TInput>` C#), almak gerekli olmayacak biçimde `Add` yöntemi için belirli oluşturulan türü. Kullanamazsınız <xref:System.Type.GetMethod%2A> bu almak için yöntemi <xref:System.Reflection.MethodInfo> doğrudan `icollOfTInput`, çünkü <xref:System.Type.GetMethod%2A> ile oluşturulan bir türü desteklemiyor. bir <xref:System.Reflection.Emit.GenericTypeParameterBuilder>. Bunun yerine, çağrı <xref:System.Type.GetMethod%2A> üzerinde `icoll`, genel tür tanımı içeren <xref:System.Collections.Generic.ICollection%601> genel arabirim. Ardından <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> `static` yöntemini üretmeye <xref:System.Reflection.MethodInfo> oluşturulan türü için. Aşağıdaki kod bu gösterir.  
  
     [!code-csharp[GenericMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#12)]
     [!code-vb[GenericMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#12)]  
  
5.  Başlatmak için kod yayma `index` değişken, 32 bit tamsayı 0 yükleniyor ve değişkende depolayarak. Etiket şube kodu yayma `enterLoop`. Döngünün içinde olduğu için bu etiket henüz, işaretlendi değil. Döngü kodunu sonraki adımda yayınlanır.  
  
     [!code-csharp[GenericMethodHowTo#32](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#32)]
     [!code-vb[GenericMethodHowTo#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#32)]  
  
6.  Döngünün kod yayma. Döngü üstündeki çağırarak işaretlemek için ilk adımdır <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> ile `loopAgain` etiketi. Etiket branch deyimleri artık bu noktaya kodda dal. Göndermek için sonraki adımdır `TOutput` için cast nesne `ICollection(Of TInput)`, yığına. Hemen gerekli değildir, ancak çağırma konumda olması gereken `Add` yöntemi. Giriş dizisi yığına gönderilen sonraki sonra `index` diziye geçerli dizini içeren değişken. <xref:System.Reflection.Emit.OpCodes.Ldelem> Opcode dizin ve dizi yığından POP ve dizinlenmiş dizi öğesi yığına iter. Yığın çağrısı için hazır <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemi, koleksiyon ve yeni bir öğesi yığından POP ve öğeyi koleksiyona ekler.  
  
     Döngü kodda kalan döngü tamamlanmış olup olmadığını görmek için sınar ve dizin artırır: dizin ve 32 bit tamsayı 1 yığına gönderilir ve eklenen, yığında; toplam bırakarak sum depolanan `index`. <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> döngü için giriş noktası olarak bu noktasını ayarlamak için çağrılır. Dizini yeniden yüklenir. Giriş dizisi yığında gönderilir ve <xref:System.Reflection.Emit.OpCodes.Ldlen> uzunluğu almak için yayınlanır. Dizin ve uzunluk yığında sunulmuştur ve <xref:System.Reflection.Emit.OpCodes.Clt> bunları Karşılaştırılacak yayınlanır. Dizinin uzunluğundan az ise <xref:System.Reflection.Emit.OpCodes.Brtrue_S> dalları geri döngü başlangıcı.  
  
     [!code-csharp[GenericMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#13)]
     [!code-vb[GenericMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#13)]  
  
7.  Göndermek için kod yayma `TOutput` nesne yığına ve elde edilen yöntemi döndürür. Yerel değişkenler `retVal` ve `ic` hem de yeni başvuru içeren `TOutput`; `ic` kullanılan erişmek için yalnızca <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemi.  
  
     [!code-csharp[GenericMethodHowTo#33](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#33)]
     [!code-vb[GenericMethodHowTo#33](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#33)]  
  
<a name="procedureSection2"></a>   
### <a name="to-invoke-the-generic-method"></a>Genel yöntemi çağırma  
  
1.  `Factory` bir genel yöntem tanımıdır. Bunu çağırmak için türleri için genel tür parametreleri atamanız gerekir. Kullanım <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> Bunu yapmak için yöntem. Aşağıdaki kod bir oluşturulmuş genel yöntem oluşturur belirtme <xref:System.String> için `TInput` ve `List(Of String)` (`List<string>` C#) için `TOutput`ve yönteminin bir dize gösterimi görüntüler.  
  
     [!code-csharp[GenericMethodHowTo#21](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#21)]
     [!code-vb[GenericMethodHowTo#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#21)]  
  
2.  Yöntem geç bağlama çağırmak için <xref:System.Reflection.MethodBase.Invoke%2A> yöntemi. Aşağıdaki kod bir dizi oluşturur <xref:System.Object>tek alt öğesi olarak içeren bir dizeler dizisi ve genel yöntemi için bağımsız değişken listesi olarak geçirir. Öğesinin ilk parametresi <xref:System.Reflection.MethodBase.Invoke%2A> yöntemi null bir başvuru olduğundan `static`. Dönüş değeri için cast `List(Of String)`, ve ilk öğe görüntülenir.  
  
     [!code-csharp[GenericMethodHowTo#22](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#22)]
     [!code-vb[GenericMethodHowTo#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#22)]  
  
3.  Bir temsilci kullanarak yöntemini çağırmak için oluşturulan genel yöntem imzası eşleşen bir temsilci olması gerekir. Bunu yapmak için kolay bir yol genel temsilcisi oluşturmaktır. Aşağıdaki kod genel temsilcisi örneği oluşturur `D` örnek kodda tanımlanan kullanarak <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType> yöntemi aşırı yüklemesini ve temsilcisini çağırır. Temsilciler geç bağlama çağrıları daha iyi gerçekleştirin.  
  
     [!code-csharp[GenericMethodHowTo#23](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#23)]
     [!code-vb[GenericMethodHowTo#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#23)]  
  
4.  Verilmiş yöntemi de kaydedilmiş derlemeye başvuran bir programdan çağrılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneğinde bir nongeneric türü oluşturur `DemoType`, genel bir yöntem `Factory`. Bu yöntem iki genel tür parametreleri olan `TInput` giriş türünü belirtin ve `TOutput` çıkış türünü belirtmek için. `TOutput` Uygulamak için tür parametresi kısıtlı `ICollection<TInput>` (`ICollection(Of TInput)` Visual Basic'te), bir başvuru türü olması ve parametresiz bir oluşturucuya sahip.  
  
 Bir dizi bir biçimsel parametresi yöntemi vardır, `TInput`. Yöntem örneği döndürür `TOutput` giriş dizinin tüm öğeleri içerir. `TOutput` uygulayan herhangi bir genel koleksiyon türü olabilir <xref:System.Collections.Generic.ICollection%601> genel arabirim.  
  
 Kod çalıştırıldığında dinamik derleme DemoGenericMethod1.dll kaydedilir ve kullanarak incelenebilir [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).  
  
> [!NOTE]
>  Kod yayma öğrenmek için iyi bir şekilde yayma ve derleyici tarafından üretilen MSIL incelemek için ayrıştırıcı kullanın çalıştığınız görevi gerçekleştiren bir Visual Basic, C# veya Visual C++ programı yazmaktır.  
  
 Kod örneği verilmiş yöntemi eşdeğerdir kaynak kodunu içerir. Geç bağlama verilmiş yöntemi çağrılır ve ayrıca kullanarak genel bir temsilci aşağıdaki kod örneğinde bildirilmedi.  
  
 [!code-csharp[GenericMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#1)]
 [!code-vb[GenericMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   C# kodunu `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.  
  
-   Hiçbir ek derleme başvurularını gereklidir.  
  
-   Csc.exe, vbc.exe veya cl.exe kullanarak komut satırında kodu derleyin. Visual Studio'da Kodu derlemek için bir konsol uygulama projesi şablonunda yerleştirin.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Reflection.Emit.MethodBuilder>  
 [Nasıl yapılır: Yansıma Yayma ile Genel Tür Tanımlama](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)
