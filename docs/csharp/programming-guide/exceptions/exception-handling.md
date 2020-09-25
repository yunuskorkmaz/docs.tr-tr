---
title: Özel durum Işleme-C# Programlama Kılavuzu
description: Özel durum işleme hakkında bilgi edinin. Try-catch, try-finally ve try-catch-finally deyimlerinin örneklerine bakın.
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: 8f7dc027396e327f08a591ced6bd6df176a17606
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91178690"
---
# <a name="exception-handling-c-programming-guide"></a>Özel Durum İşleme (C# Programlama Kılavuzu)

[TRY](../../language-reference/keywords/try-catch.md) bloğu, C# programcıları tarafından bir özel durumdan etkilenebilecek kodu bölümlemek için kullanılır. İlişkili [catch](../../language-reference/keywords/try-catch.md) blokları, ortaya çıkan özel durumları işlemek için kullanılır. [Finally](../../language-reference/keywords/try-finally.md) bloğu bloğunda bir özel durum oluşturulup oluşturulmayacağını (blokta `try` ayrılan kaynakları serbest bırakma gibi) ne olursa olsun, çalıştırılan kodu içerir `try` . Bir `try` blok, bir veya daha fazla ilişkili `catch` blok, ya da bir `finally` blok ya da her ikisini gerektirir.  
  
 Aşağıdaki örneklerde bir `try-catch` ifade, bir `try-finally` ifade ve bir `try-catch-finally` ifade gösterilmektedir.  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 `try`Or bloğu olmayan bir blok bir `catch` `finally` derleyici hatasına neden olur.  
  
## <a name="catch-blocks"></a>Catch blokları  

 Bir `catch` blok, yakalamak için özel durum türünü belirtebilir. Tür belirtimine *özel durum filtresi*denir. Özel durum türü öğesinden türetilmelidir <xref:System.Exception> . Genel olarak, <xref:System.Exception> blokta oluşturulan tüm özel durumları nasıl işleyebileceğinizi `try` veya bloizin sonuna bir [throw](../../language-reference/keywords/throw.md) bildirisi eklemiş olmanız durumunda özel durum filtresi olarak belirtmeyin `catch` .  
  
 `catch`Farklı özel durum filtrelerine sahip birden çok blok birbirine zincirlenebilir. `catch`Bloklar kodunuzda yukarıdan aşağıya değerlendirilir, ancak `catch` oluşturulan her özel durum için yalnızca bir blok yürütülür. `catch`Oluşturulan özel durumun tam türünü veya temel sınıfını belirten ilk blok yürütülür. Bir `catch` blok eşleşen bir özel durum filtresi belirtiyorsa, `catch` deyimde varsa, filtre olmayan bir blok seçilir. `catch`Blokları en belirli (yani, en türetilmiş) özel durum türleri ile konumlandırmak önemlidir.  
  
 Aşağıdaki koşullar doğru olduğunda özel durumları yakalamalı:  
  
- Özel durumun neden oluşturulması gerektiği hakkında daha iyi bir fikir sahibi olabilirsiniz ve bir nesneyi yakalarsanız kullanıcıdan yeni bir dosya adı girmesini isteme gibi belirli bir kurtarma uygulayabilirsiniz <xref:System.IO.FileNotFoundException> .  
  
- Yeni, daha özel bir özel durum oluşturabilir ve silebilirsiniz.  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- Ek işleme için geçirmeden önce bir özel durumu kısmen işlemek istiyorsunuz. Aşağıdaki örnekte, `catch` özel durumu yeniden oluşturmadan önce bir hata günlüğüne giriş eklemek için bir blok kullanılır.  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Finally blokları  

 Bir `finally` blok, bir blokta gerçekleştirilen eylemleri temizlemenize olanak sağlar `try` . Varsa, blok `finally` ve eşleşen bloğundan sonra blok son yürütülür `try` `catch` . Bir `finally` blok her zaman bir özel durum oluşturulup oluşturulmayacağını veya `catch` özel durum türüyle eşleşen bir blok bulunup bulunamadığına bakılmaksızın çalışır.  
  
 `finally`Blok, çalışma zamanındaki çöp toplayıcısının nesneleri son haline getirilmeksizin dosya akışları, veritabanı bağlantıları ve grafik tanıtıcıları gibi kaynakları serbest bırakmak için kullanılabilir. Daha fazla bilgi için bkz. [using deyimleri](../../language-reference/keywords/using-statement.md) .  
  
 Aşağıdaki örnekte, bloğu `finally` bloğunda açılan bir dosyayı kapatmak için kullanılır `try` . Dosya tutamacı durumunun, dosya kapatılmadan önce denetlendiğine dikkat edin. `try`Blok dosyayı açmayabilir, dosya tanıtıcısı yine de değeri içerir `null` ve `finally` blok bunu kapatmayı denemez. Alternatif olarak, dosya blokta başarıyla açılırsa `try` , `finally` blok açık dosyayı kapatır.  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Exceptions](~/_csharplang/spec/exceptions.md) ve [TRY deyimleri](~/_csharplang/spec/statements.md#the-try-statement) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# başvurusu](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../index.md)
- [Özel durumlar ve özel durum Işleme](./index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using Deyimi](../../language-reference/keywords/using-statement.md)
