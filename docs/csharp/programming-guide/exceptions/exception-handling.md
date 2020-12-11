---
title: Özel durum Işleme-C# Programlama Kılavuzu
description: Özel durum işleme hakkında bilgi edinin. Try-catch, try-finally ve try-catch-finally deyimlerinin örneklerine bakın.
ms.date: 12/09/2020
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: fabf1413ba498232e67f45460195fe96e25fab0a
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110201"
---
# <a name="exception-handling-c-programming-guide"></a>Özel Durum İşleme (C# Programlama Kılavuzu)

[TRY](../../language-reference/keywords/try-catch.md) bloğu, C# programcıları tarafından bir özel durumdan etkilenebilecek kodu bölümlemek için kullanılır. İlişkili [catch](../../language-reference/keywords/try-catch.md) blokları, ortaya çıkan özel durumları işlemek için kullanılır. [Finally](../../language-reference/keywords/try-finally.md) bloğu bloğunda bir özel durumun oluşturulup oluşturulmayacağını, blok içinde `try` ayrılan kaynakları serbest bırakma gibi çalışır `try` . Bir `try` blok, bir veya daha fazla ilişkili `catch` blok, ya da bir `finally` blok ya da her ikisini gerektirir.

Aşağıdaki örneklerde bir `try-catch` ifade, bir `try-finally` ifade ve bir `try-catch-finally` ifade gösterilmektedir.

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryCatchStructure":::

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryFinallyStructure":::

:::code language="csharp" source="snippets/exceptions/Program.cs" id="TryCatchFinallyStructure":::

`try`Or bloğu olmayan bir blok bir `catch` `finally` derleyici hatasına neden olur.

## <a name="catch-blocks"></a>Catch blokları

Bir `catch` blok, yakalamak için özel durum türünü belirtebilir. Tür belirtimine *özel durum filtresi* denir. Özel durum türü öğesinden türetilmelidir <xref:System.Exception> . Genel olarak, <xref:System.Exception> blokta oluşturulmuş olabilecek tüm özel durumları nasıl işleyebileceğinizi `try` veya bloizin sonuna bir [throw](../../language-reference/keywords/throw.md) bildirisi eklemiş olmanız durumunda özel durum filtresi olarak belirtmeyin `catch` .

`catch`Farklı özel durum sınıflarına sahip birden çok blok birlikte zincirlenebilir. `catch`Bloklar kodunuzda yukarıdan aşağıya değerlendirilir, ancak `catch` oluşturulan her özel durum için yalnızca bir blok yürütülür. `catch`Oluşturulan özel durumun tam türünü veya temel sınıfını belirten ilk blok yürütülür. Herhangi bir `catch` blok eşleşen bir özel durum sınıfı belirtiyorsa, `catch` deyimde varsa herhangi bir tür içermeyen bir blok seçilir. `catch`Blokları en özel (yani en türetilmiş) özel durum sınıflarıyla konumlandırmak önemlidir.

Aşağıdaki koşullar doğru olduğunda özel durumları yakala:

- Özel durumun neden oluşturulması gerektiği hakkında daha iyi bir fikir sahibi olabilirsiniz ve bir nesneyi yakalarsanız kullanıcıdan yeni bir dosya adı girmesini isteme gibi belirli bir kurtarma uygulayabilirsiniz <xref:System.IO.FileNotFoundException> .
- Yeni, daha özel bir özel durum oluşturabilir ve silebilirsiniz.
  :::code language="csharp" source="snippets/exceptions/Program.cs" id="ThrowMoreSpecificException":::
- Ek işleme için geçirmeden önce bir özel durumu kısmen işlemek istiyorsunuz. Aşağıdaki örnekte, `catch` özel durum yeniden oluşturulmadan önce bir hata günlüğüne giriş eklemek için bir blok kullanılır.
  :::code language="csharp" source="snippets/exceptions/Program.cs" id="RethrowError":::

Catch yan tümcesine bir Boole ifadesi eklemek için *özel durum filtreleri* de belirtebilirsiniz. Bu, belirli bir catch yan tümcesinin yalnızca bu koşul doğru olduğunda eşleştiğini gösterir. Aşağıdaki örnekte her iki catch yan tümcesi de aynı özel durum sınıfını kullanır, ancak farklı bir hata iletisi oluşturmak için ek bir koşul denetlenir:

:::code language="csharp" source="snippets/exceptions/ExceptionFilter.cs" ID="DemonstrateExceptionFilter":::

Her zaman geri döndürülen bir özel durum filtresi `false` , tüm özel durumları incelemek için kullanılabilir ancak bunları işlemez. Yaygın olarak kullanılan bir kullanım özel durumları günlüğe kaydeder:

:::code language="csharp" source="snippets/exceptions/ExceptionFilter.cs" ID="ShowExceptionFilter":::

`LogException`Yöntemi her zaman döndürülür `false` , `catch` Bu özel durum filtresi ile eşleşen yan tümce yoktur. Catch yan tümcesi genel, using <xref:System.Exception?displayProperty=nameWithType> ve sonraki yan tümceleri daha belirli özel durum sınıflarını işleyebilir.

## <a name="finally-blocks"></a>Finally blokları

Bir `finally` blok, bir blokta gerçekleştirilen eylemleri temizlemenize olanak sağlar `try` . Varsa, blok `finally` ve eşleşen bloğundan sonra blok son yürütülür `try` `catch` . Bir `finally` blok her zaman çalışır, bir özel durum oluşturulur veya `catch` özel durum türüyle eşleşen bir blok bulunur.

`finally`Blok, çalışma zamanındaki çöp toplayıcısının nesneleri son haline getirilmeksizin dosya akışları, veritabanı bağlantıları ve grafik tanıtıcıları gibi kaynakları serbest bırakmak için kullanılabilir. Daha fazla bilgi için [using bildirimine](../../language-reference/keywords/using-statement.md)bakın.

Aşağıdaki örnekte, bloğu `finally` bloğunda açılan bir dosyayı kapatmak için kullanılır `try` . Dosya tutamacı durumunun, dosya kapatılmadan önce denetlendiğine dikkat edin. `try`Blok dosyayı açmazsa dosya tanıtıcısı yine de değeri içerir `null` ve `finally` blok bunu kapatmayı denemez. Bunun yerine, dosya bloğunda başarıyla açılırsa `try` , `finally` blok açık dosyayı kapatır.

:::code language="csharp" source="snippets/exceptions/Program.cs" id="CleanupIfNotNull":::

## <a name="c-language-specification"></a>C# Dil Belirtimi

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Exceptions](~/_csharplang/spec/exceptions.md) ve [TRY deyimleri](~/_csharplang/spec/statements.md#the-try-statement) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../language-reference/index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using Deyimi](../../language-reference/keywords/using-statement.md)
