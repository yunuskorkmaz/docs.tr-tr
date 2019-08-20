---
title: Özel durum Işleme C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: 5013738e74aaa260ab6f5bcd4d73904cfbdcc3c8
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590272"
---
# <a name="exception-handling-c-programming-guide"></a>Özel Durum İşleme (C# Programlama Kılavuzu)
[TRY](../../language-reference/keywords/try-catch.md) bloğu, programcılar tarafından C# bir özel durumdan etkilenebilecek kodu bölümlemek için kullanılır. İlişkili [catch](../../language-reference/keywords/try-catch.md) blokları, ortaya çıkan özel durumları işlemek için kullanılır. [Finally](../../language-reference/keywords/try-finally.md) bloğu bloğunda bir özel durum `try` oluşturulup oluşturulmayacağını (blokta ayrılan `try` kaynakları serbest bırakma gibi) ne olursa olsun, çalıştırılan kodu içerir. Bir `try` blok, bir veya daha fazla `catch` ilişkili blok, ya `finally` da bir blok ya da her ikisini gerektirir.  
  
 Aşağıdaki örneklerde bir `try-catch` ifade, bir `try-finally` ifade ve bir `try-catch-finally` ifade gösterilmektedir.  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 Or`catch` `try` bloğuolmayanbirblokbirderleyici`finally` hatasına neden olur.  
  
## <a name="catch-blocks"></a>Catch blokları  
 Bir `catch` blok, yakalamak için özel durum türünü belirtebilir. Tür belirtimine *özel durum filtresi*denir. Özel durum türü öğesinden <xref:System.Exception>türetilmelidir. Genel olarak, `try` blokta oluşturulan tüm <xref:System.Exception> özel durumları nasıl işleyebileceğinizi veya bloizin `catch` sonuna bir [throw](../../language-reference/keywords/throw.md) bildirisi eklemiş olmanız durumunda özel durum filtresi olarak belirtmeyin.  
  
 Farklı `catch` özel durum filtrelerine sahip birden çok blok birbirine zincirlenebilir. Bloklar kodunuzda yukarıdan aşağıya değerlendirilir, ancak oluşturulan her özel durum için yalnızca bir `catch` blok yürütülür. `catch` Oluşturulan özel `catch` durumun tam türünü veya temel sınıfını belirten ilk blok yürütülür. Bir blok eşleşen bir özel durum filtresi belirtiyorsa, deyimde varsa, filtre olmayan bir `catch` blok seçilir. `catch` Blokları en belirli (yani `catch` , en türetilmiş) özel durum türleri ile konumlandırmak önemlidir.  
  
 Aşağıdaki koşullar doğru olduğunda özel durumları yakalamalı:  
  
- Özel durumun neden oluşturulması gerektiği hakkında daha iyi bir fikir sahibi olabilirsiniz ve bir <xref:System.IO.FileNotFoundException> nesneyi yakalarsanız kullanıcıdan yeni bir dosya adı girmesini isteme gibi belirli bir kurtarma uygulayabilirsiniz.  
  
- Yeni, daha özel bir özel durum oluşturabilir ve silebilirsiniz.  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- Ek işleme için geçirmeden önce bir özel durumu kısmen işlemek istiyorsunuz. Aşağıdaki örnekte, özel durumu yeniden `catch` oluşturmadan önce bir hata günlüğüne giriş eklemek için bir blok kullanılır.  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Finally blokları  
 Bir `finally` blok, bir `try` blokta gerçekleştirilen eylemleri temizlemenize olanak sağlar. Varsa, `finally` blok ve eşleşen `catch` bloğundan `try` sonra blok son yürütülür. Bir `finally` blok her zaman bir özel durum oluşturulup oluşturulmayacağını veya özel durum türüyle eşleşen `catch` bir blok bulunup bulunamadığına bakılmaksızın çalışır.  
  
 `finally` Blok, çalışma zamanındaki çöp toplayıcısının nesneleri son haline getirilmeksizin dosya akışları, veritabanı bağlantıları ve grafik tanıtıcıları gibi kaynakları serbest bırakmak için kullanılabilir. Daha fazla bilgi için bkz. [using deyimleri](../../language-reference/keywords/using-statement.md) .  
  
 Aşağıdaki örnekte, `finally` bloğu `try` bloğunda açılan bir dosyayı kapatmak için kullanılır. Dosya tutamacı durumunun, dosya kapatılmadan önce denetlendiğine dikkat edin. Blok dosyayı açmayabilir, dosya tanıtıcısı yine de değeri `null` içerir ve `finally` blok bunu kapatmayı denemez. `try` Alternatif olarak, dosya `try` blokta başarıyla açılırsa `finally` , blok açık dosyayı kapatır.  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../../language-reference/language-specification/index.md) [Exceptions](~/_csharplang/spec/exceptions.md) ve [TRY deyimleri](~/_csharplang/spec/statements.md#the-try-statement) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using Deyimi](../../language-reference/keywords/using-statement.md)
