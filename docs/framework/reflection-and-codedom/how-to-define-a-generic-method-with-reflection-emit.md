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
ms.openlocfilehash: 49c490b57574f8c9c9c93e3e0da2089cec95481f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59344240"
---
# <a name="how-to-define-a-generic-method-with-reflection-emit"></a>Nasıl yapılır: Yansıma Yayma ile Genel Yöntem Tanımlama
İlk yordamda, iki tür parametreleri ile basit bir genel yöntem oluşturulacağını ve tür parametreleri için sınıf kısıtlamaları, arabirim kısıtlamasını ve özel kısıtlamalar uygulamak nasıl gösterir.  
  
 İkinci yordam, yöntem gövdesini yayma konusunda ve yöntemin genel tür parametreleri genel türlerin örneklerini oluşturmak için ve kendi yöntemlerini çağırmak için nasıl kullanılacağını gösterir.  
  
 Üçüncü yordamı, genel yöntemi çağırma işlemi gösterilmektedir.  
  
> [!IMPORTANT]
>  Bir yöntem genel değil, çünkü yalnızca genel bir türe ait ve bu türdeki tür parametreleri kullanır. Bir yalnızca kendi tür parametresi listesi varsa genel yöntemdir. Bu örnekte olduğu gibi jenerik olmayan bir türe göre genel bir yöntem görünür. Genel tür jenerik olmayan bir yöntem bir örnek için bkz [nasıl yapılır: Yansıma ile genel tür tanımlama yayma](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md).  
  
### <a name="to-define-a-generic-method"></a>Genel bir yöntemi tanımlamak için  
  
1. Başlamadan önce genel yöntem yüksek seviye dil kullanan yazılırken görüntülenme şeklini konumunda aramak kullanışlıdır. Aşağıdaki kod genel yöntem çağırmak için kod ile birlikte bu konu için örnek kod dahil edilir. Yöntemi iki tür parametreleri olan `TInput` ve `TOutput`hangisinin bir başvuru türü olmalıdır ikinci (`class`), parametresiz bir oluşturucusu olmalıdır (`new`) ve uygulamalıdır `ICollection(Of TInput)` (`ICollection<TInput>` C#). Bu arabirim kısıtlaması sağlar <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemi, öğeleri eklemek için kullanılabilir `TOutput` yöntemi oluşturur koleksiyonu. Yöntem bir biçimsel parametreye sahip `input`, bir dizi olduğu `TInput`. Yöntem türü bir koleksiyon oluşturur `TOutput` ve öğelerini kopyalar `input` koleksiyonuna.  
  
     [!code-csharp[GenericMethodHowTo#20](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#20)]
     [!code-vb[GenericMethodHowTo#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#20)]  
  
2. Dinamik derleme tanımlama ve genel yöntem türü içermesi için dinamik bir modüle ait. Bu durumda, derlemeyi adlı yalnızca bir modül olan `DemoMethodBuilder1`, ve modül adı bütünleştirilmiş kod adına ek uzantı aynıdır. Bu örnekte, derleme diske kaydedilir ve ayrıca, bunu <xref:System.Reflection.Emit.AssemblyBuilderAccess.RunAndSave?displayProperty=nameWithType> belirtilir. Kullanabileceğiniz [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) DemoMethodBuilder1.dll inceleyin ve 1. adımda gösterilen yöntemin Microsoft Ara dili (MSIL) karşılaştırın.  
  
     [!code-csharp[GenericMethodHowTo#2](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#2)]
     [!code-vb[GenericMethodHowTo#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#2)]  
  
3. Ait genel yöntem türü tanımlar. Türü genel olması gerekmez. Genel yöntem ya da bir genel ya da jenerik olmayan türe ait olabilir. Bu örnekte, türü bir sınıf, genel değil ve adlı `DemoType`.  
  
     [!code-csharp[GenericMethodHowTo#3](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#3)]
     [!code-vb[GenericMethodHowTo#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#3)]  
  
4. Genel yöntem tanımlayın. Genel yöntem genel tür parametrelerle genel yöntemin biçimsel parametre türleri belirtilmişse kullanın <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%28System.String%2CSystem.Reflection.MethodAttributes%29> yöntemi tanımlamak için yöntem aşırı yüklemesi. Çağrısında yöntemin biçimsel parametre türlerini belirtemezsiniz yöntemin genel tür parametrelerini henüz, tanımlanmayan <xref:System.Reflection.Emit.TypeBuilder.DefineMethod%2A>. Bu örnekte, yöntem adlı `Factory`. Genel bir yöntemdir ve `static` (`Shared` Visual Basic'te).  
  
     [!code-csharp[GenericMethodHowTo#4](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#4)]
     [!code-vb[GenericMethodHowTo#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#4)]  
  
5. Genel tür parametrelerini tanımlayın `DemoMethod` için parametre adlarını içeren bir dize dizisi geçirerek <xref:System.Reflection.Emit.MethodBuilder.DefineGenericParameters%2A?displayProperty=nameWithType> yöntemi. Bu yöntem genel bir yöntem sağlar. Aşağıdaki kod yapar `Factory` tür parametreleri ile genel yöntem `TInput` ve `TOutput`. Kodun okunmasını kolaylaştırmak için bu adlar değişkenlerle tutmak için oluşturulan <xref:System.Reflection.Emit.GenericTypeParameterBuilder> iki tür parametreleri temsil eden nesneleri.  
  
     [!code-csharp[GenericMethodHowTo#5](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#5)]
     [!code-vb[GenericMethodHowTo#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#5)]  
  
6. İsteğe bağlı olarak özel kısıtlamalar için tür parametreleri ekleyin. Özel kısıtlamalar kullanarak eklenir <xref:System.Reflection.Emit.GenericTypeParameterBuilder.SetGenericParameterAttributes%2A> yöntemi. Bu örnekte, `TOutput` bir başvuru türü olması ve parametresiz bir oluşturucuya sahip sınırlıdır.  
  
     [!code-csharp[GenericMethodHowTo#6](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#6)]
     [!code-vb[GenericMethodHowTo#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#6)]  
  
7. İsteğe bağlı olarak, sınıf ve arabirim kısıtlamaları için tür parametreleri ekleyin. Bu örnekte, tür parametresi `TOutput` uygulayan türler için kısıtlı `ICollection(Of TInput)` (`ICollection<TInput>` içinde C#) arabirimi. Bu, sağlar <xref:System.Collections.Generic.ICollection%601.Add%2A> yöntemi, öğeleri eklemek için kullanılabilir.  
  
     [!code-csharp[GenericMethodHowTo#7](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#7)]
     [!code-vb[GenericMethodHowTo#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#7)]  
  
8. Biçimsel parametre yöntemin tanımlamak kullanarak <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> yöntemi. Bu örnekte, `Factory` yöntemi olan bir parametre dizisi `TInput`. Bu tür çağrılarak oluşturulan <xref:System.Type.MakeArrayType%2A> metodunda <xref:System.Reflection.Emit.GenericTypeParameterBuilder> temsil eden `TInput`. Bağımsız değişkenin <xref:System.Reflection.Emit.MethodBuilder.SetParameters%2A> dizisidir <xref:System.Type> nesneleri.  
  
     [!code-csharp[GenericMethodHowTo#8](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#8)]
     [!code-vb[GenericMethodHowTo#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#8)]  
  
9. Yöntemi için dönüş türü tanımlayan kullanarak <xref:System.Reflection.Emit.MethodBuilder.SetReturnType%2A> yöntemi. Bu örnekte, bir örneğini `TOutput` döndürülür.  
  
     [!code-csharp[GenericMethodHowTo#9](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#9)]
     [!code-vb[GenericMethodHowTo#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#9)]  
  
10. Yöntem yaymak kullanarak, gövde <xref:System.Reflection.Emit.ILGenerator>. Ayrıntılar için yöntem gövdesini yayma için eşlik eden yordamına bakın.  
  
    > [!IMPORTANT]
    >  Genel türlerin yöntemlere yapılan çağrılar yayma ve bu türlerin tür bağımsız değişkenlerini yöntemin genel tür parametrelerini olduğunda kullanmalısınız `static` <xref:System.Reflection.Emit.TypeBuilder.GetConstructor%28System.Type%2CSystem.Reflection.ConstructorInfo%29>, <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29>, ve <xref:System.Reflection.Emit.TypeBuilder.GetField%28System.Type%2CSystem.Reflection.FieldInfo%29> yöntemi aşırı yüklemeleri <xref:System.Reflection.Emit.TypeBuilder> sınıfı oluşturulan form yöntemlerin edinin. Bu yöntem gövdesini yayma eşlik eden yordamı gösterir.  
  
11. Yöntemi içeren türünü tamamlamak ve bütünleştirilmiş kodu kaydedin. Genel yöntem çağırma için eşlik eden yordamı tamamlanmış yöntemini çağırmak için iki yolunu gösterir.  
  
     [!code-csharp[GenericMethodHowTo#14](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#14)]
     [!code-vb[GenericMethodHowTo#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#14)]  
  
<a name="procedureSection1"></a>   
### <a name="to-emit-the-method-body"></a>Yöntem gövdesini yaymak için  
  
1. Bir kod oluşturucuyu alın ve yerel değişkenleri ve etiketleri bildirin. <xref:System.Reflection.Emit.ILGenerator.DeclareLocal%2A> Yöntemi, yerel değişkenler bildirmek için kullanılır. `Factory` Yöntemi dört yerel değişkenleri vardır: `retVal` yeni tutacak `TOutput` yöntemi tarafından döndürülen `ic` tutacak `TOutput` zaman bunu dönüştürüldü `ICollection(Of TInput)` (`ICollection<TInput>` içinde C#), `input`oluşan Giriş dizisinin tutacak `TInput` nesneleri ve `index` dizi aracılığıyla yineleme yapmak için. Yöntemi de döngüye girme iki etiket vardır (`enterLoop`) ve bir döngünün en üst (`loopAgain`), tanımlı kullanarak <xref:System.Reflection.Emit.ILGenerator.DefineLabel%2A> yöntemi.  
  
     Yöntemi yapacağı ilk şey, kendi bağımsız değişkenini kullanarak yüklemek için olan <xref:System.Reflection.Emit.OpCodes.Ldarg_0> opcode yerel değişkende depolamak için `input` kullanarak <xref:System.Reflection.Emit.OpCodes.Stloc_S> opcode.  
  
     [!code-csharp[GenericMethodHowTo#10](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#10)]
     [!code-vb[GenericMethodHowTo#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#10)]  
  
2. Bir örneğini oluşturmak için kod yayan `TOutput`, genel yöntem aşırı yüklemesini kullanarak <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> yöntemi. Bu aşırı yüklemesi kullanarak belirtilen türün parametresiz bir oluşturucuya sahip gerektirir, bu kısıtlama eklemek için neden olduğu `TOutput`. Oluşturulan genel yöntem geçirerek oluşturun `TOutput` için <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A>. Yöntem çağırmak için kod yayan sonra yerel değişkende depolamak üzere kod yayma `retVal` kullanma <xref:System.Reflection.Emit.OpCodes.Stloc_S>  
  
     [!code-csharp[GenericMethodHowTo#11](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#11)]
     [!code-vb[GenericMethodHowTo#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#11)]  
  
3. Yeni bir şekilde kod yayan `TOutput` nesnesini `ICollection(Of TInput)` ve yerel değişkende saklayın `ic`.  
  
     [!code-csharp[GenericMethodHowTo#31](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#31)]
     [!code-vb[GenericMethodHowTo#31](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#31)]  
  
4. Alma bir <xref:System.Reflection.MethodInfo> temsil eden <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemi. Yöntem üzerinde çalışan bir `ICollection(Of TInput)` (`ICollection<TInput>` içinde C#) almak gerekli olan bu nedenle `Add` yöntemi için belirli bir yapıda türü. Kullanamazsınız <xref:System.Type.GetMethod%2A> için bu yöntemi <xref:System.Reflection.MethodInfo> doğrudan `icollOfTInput`, çünkü <xref:System.Type.GetMethod%2A> ile oluşturulmuş bir türü desteklenmiyor bir <xref:System.Reflection.Emit.GenericTypeParameterBuilder>. Bunun yerine çağrı <xref:System.Type.GetMethod%2A> üzerinde `icoll`, genel tür tanımı içeren <xref:System.Collections.Generic.ICollection%601> genel arabirim. Ardından <xref:System.Reflection.Emit.TypeBuilder.GetMethod%28System.Type%2CSystem.Reflection.MethodInfo%29> `static` üretmek için yöntemi <xref:System.Reflection.MethodInfo> için yapılandırılmış türdedir. Aşağıdaki kod bunu gösterir.  
  
     [!code-csharp[GenericMethodHowTo#12](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#12)]
     [!code-vb[GenericMethodHowTo#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#12)]  
  
5. Başlatmak için kod yayan `index` değişken, 32 bit tam sayı 0'ı yükleme ve bir değişkende depolanması. Kod etiketine dalına yayma `enterLoop`. Döngünün içinde olduğundan bu etiket henüz, işaretlenen değil. Sonraki adımda döngüsü için kod yayılır.  
  
     [!code-csharp[GenericMethodHowTo#32](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#32)]
     [!code-vb[GenericMethodHowTo#32](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#32)]  
  
6. Döngü için kod üretir. Çağırarak döngünün en üstüne işaretlemek için ilk adımıdır <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> ile `loopAgain` etiketi. Etiket dal deyimleri artık bu kod noktasına dallara. Göndermek için sonraki adımdır `TOutput` nesne başvurusuna `ICollection(Of TInput)`, yığına. Hemen gerekli değildir, ancak arama konumu olmalıdır `Add` yöntemi. Giriş dizisinin yığın üstüne gönderilen İleri sonra `index` diziye geçerli dizini içeren bir değişkeni. <xref:System.Reflection.Emit.OpCodes.Ldelem> Opcode dizini ve dizinin yığından POP ve sıralı dizinin öğe yığına iter. Yığın için yapılan çağrının hazırdır <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemi, koleksiyon ve yeni bir öğe yığından POP ve öğeyi koleksiyona ekler.  
  
     Dizin ve döngü bitip bitmediğini görmek için sınar döngüsünde kodun geri kalanını artırır: Dizin ve 32-bit tamsayı 1 yığına itildi ve eklenen, yığında; toplamı çıkılıyor Toplam depolanan `index`. <xref:System.Reflection.Emit.ILGenerator.MarkLabel%2A> döngü için giriş noktası olarak bu noktası ayarlamak için çağrılır. Dizin yeniden yüklenir. Giriş dizisinin yığına itilir ve <xref:System.Reflection.Emit.OpCodes.Ldlen> uzunluğunu almak için yayılır. Dizin ve uzunluk yığına sunulmuştur ve <xref:System.Reflection.Emit.OpCodes.Clt> karşılaştırma yayılır. Dizinin uzunluğundan küçükse <xref:System.Reflection.Emit.OpCodes.Brtrue_S> dallar geri döngü başlangıcına.  
  
     [!code-csharp[GenericMethodHowTo#13](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#13)]
     [!code-vb[GenericMethodHowTo#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#13)]  
  
7. Göndermek için kod yayan `TOutput` nesne yığınına ve elde edilen yöntemi döndürür. Yerel değişkenler `retVal` ve `ic` yeni başvuruları içeren `TOutput`; `ic` kullanılan erişmek için yalnızca <xref:System.Collections.Generic.ICollection%601.Add%2A?displayProperty=nameWithType> yöntemi.  
  
     [!code-csharp[GenericMethodHowTo#33](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#33)]
     [!code-vb[GenericMethodHowTo#33](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#33)]  
  
<a name="procedureSection2"></a>   
### <a name="to-invoke-the-generic-method"></a>Genel yöntem çağırmak için  
  
1. `Factory` bir genel yöntem tanımıdır. Onu çağırmak için genel tür parametrelerinin türleri atamanız gerekir. Kullanım <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A> Bunu yapmak için yöntemi. Oluşturulmuş bir genel yöntem aşağıdaki kodu oluşturur belirtme <xref:System.String> için `TInput` ve `List(Of String)` (`List<string>` içinde C#) için `TOutput`, yöntem bir dize gösterimini görüntüler.  
  
     [!code-csharp[GenericMethodHowTo#21](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#21)]
     [!code-vb[GenericMethodHowTo#21](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#21)]  
  
2. Yöntem geç bağlanan çağırmak için <xref:System.Reflection.MethodBase.Invoke%2A> yöntemi. Aşağıdaki kod bir dizi oluşturur <xref:System.Object>yalnızca alt öğesi olarak içeren bir dizeler dizisi ve genel yöntemi için bağımsız değişken listesi olarak geçirir. İlk parametresi <xref:System.Reflection.MethodBase.Invoke%2A> yöntemdir çünkü bir null başvurudur `static`. Dönüş değeri türüne dönüştürülür `List(Of String)`, ve ilk alt öğe görüntülenir.  
  
     [!code-csharp[GenericMethodHowTo#22](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#22)]
     [!code-vb[GenericMethodHowTo#22](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#22)]  
  
3. Bir temsilci kullanarak yöntemini çağırmak için oluşturulmuş bir genel yöntem imzası eşleşen bir temsilci olmalıdır. Bunu yapmanın kolay bir yolu, bir genel temsilci oluşturmaktır. Aşağıdaki kod genel temsilci örneği oluşturur `D` örnek kod içinde tanımlanan kullanarak <xref:System.Delegate.CreateDelegate%28System.Type%2CSystem.Reflection.MethodInfo%29?displayProperty=nameWithType> yöntemi aşırı yüklemesi ve temsilci çağırır. Geç bağlama çağrıları daha iyi temsilciler gerçekleştirin.  
  
     [!code-csharp[GenericMethodHowTo#23](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#23)]
     [!code-vb[GenericMethodHowTo#23](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#23)]  
  
4. Kayıtlı bir derlemeye başvuran bir programdan yayılan yöntemi de volat pouze jednou.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod örneği jenerik olmayan bir tür oluşturur `DemoType`, genel bir yöntem ile `Factory`. Bu yöntem iki genel tür parametreleri olan `TInput` bir giriş türü belirtmek için ve `TOutput` çıktı türü belirtmek için. `TOutput` Uygulamak için tür parametresi kısıtlı `ICollection<TInput>` (`ICollection(Of TInput)` Visual Basic'te), bir başvuru türü olması ve parametresiz bir oluşturucu.  
  
 Yöntemi bir dizi olan bir biçimsel parametresi vardır, `TInput`. Yöntem bir örneğini döndürür `TOutput` , Giriş dizisinin tüm öğeleri içerir. `TOutput` uygulayan herhangi bir genel koleksiyon tür olabilir <xref:System.Collections.Generic.ICollection%601> genel arabirim.  
  
 Kod yürütüldüğünde, dinamik derlemenin DemoGenericMethod1.dll kaydedilir ve kullanarak incelenmesi [Ildasm.exe (IL ayrıştırıcı)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md).  
  
> [!NOTE]
>  Kodu yayma hakkında bilgi edinmek için en iyi yolu, bir Visual Basic yazmaktır C#, veya yayma ve ayrıştırıcı MSIL derleyici tarafından üretilen incelemek için çalıştığınız görev gerçekleştiren Visual C++ programı.  
  
 Kod örneği, yayılan yönteme eşdeğerdir kaynak kodunu içerir. Geç bağlama yayılan yöntemi çağrılır ve ayrıca kullanarak temsilci aşağıdaki kod örneğinde bildirilen.  
  
 [!code-csharp[GenericMethodHowTo#1](../../../samples/snippets/csharp/VS_Snippets_CLR/GenericMethodHowTo/CS/source.cs#1)]
 [!code-vb[GenericMethodHowTo#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/GenericMethodHowTo/VB/source.vb#1)]  
  
## <a name="compiling-the-code"></a>Kod Derleniyor  
  
-   C# kodu içeren `using` deyimleri (`Imports` Visual Basic'te) derleme için gerekli.  
  
-   Hiçbir ek derleme başvurularını gereklidir.  
  
-   Csc.exe, vbc.exe veya cl.exe kullanarak komut satırındaki kodu derleyin. Visual Studio'da Kodu derlemek için bir konsol uygulaması projesi şablonu içine koyun.  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Reflection.Emit.MethodBuilder>
- [Nasıl yapılır: Yansıma ile genel tür tanımlama yayma](../../../docs/framework/reflection-and-codedom/how-to-define-a-generic-type-with-reflection-emit.md)
