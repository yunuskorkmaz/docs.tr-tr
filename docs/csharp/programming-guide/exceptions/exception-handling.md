---
title: Özel Durum İşleme - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: ee1e5bd15183dad9ffe97824f9b194668e9d3b17
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705307"
---
# <a name="exception-handling-c-programming-guide"></a>Özel Durum İşleme (C# Programlama Kılavuzu)
Bir [try](../../language-reference/keywords/try-catch.md) bloğu C# programcıları tarafından bir özel durum tarafından etkilenebilir bölüm kodu için kullanılır. İlişkili [catch](../../language-reference/keywords/try-catch.md) blokları, ortaya çıkan özel durumları işlemek için kullanılır. [Son olarak](../../language-reference/keywords/try-finally.md) blok, `try` `try` blokta ayrılan kaynakları serbest bırakmak gibi bir özel durum bloğuna atılıp atılmadığına bakılmaksızın çalıştırılan kod içerir. Bir `try` blok bir veya `catch` daha fazla `finally` ilişkili blok veya bir blok veya her ikisini gerektirir.  
  
 Aşağıdaki örneklerde `try-catch` bir deyim, bir `try-finally` `try-catch-finally` deyim ve bir deyim gösterilmektedir.  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 Bir `try` `catch` veya `finally` blok olmayan bir blok derleyici hatasına neden olur.  
  
## <a name="catch-blocks"></a>Blokları Yakala  
 Bir `catch` blok yakalamak için özel durum türünü belirtebilir. Tür belirtimi özel *durum filtresi*olarak adlandırılır. Özel durum türü <xref:System.Exception>nden türetilmelidir. Genel <xref:System.Exception> olarak, `try` blokta atılabilecek tüm özel durumların nasıl işleyeceğini bilmediğiniz veya bloğunuzun `catch` sonuna bir [atma](../../language-reference/keywords/throw.md) deyimi eklenmiş seniz, özel durum filtresi olarak belirtmeyin.  
  
 Farklı `catch` özel durum filtreleri ile birden fazla blok birlikte zincirlenebilir. Bloklar `catch` kodunuzda yukarıdan aşağıya doğru değerlendirilir, `catch` ancak atılan her özel durum için yalnızca bir blok yürütülür. Atılan `catch` özel durum tam türünü veya taban sınıfını belirten ilk blok yürütülür. Hiçbir `catch` blok eşleşen bir özel durum `catch` filtresi belirtmezse, deyimde varsa filtresi olmayan bir blok seçilir. Blokları önce en `catch` özel (yani en türetilmiş) özel özel durum türlerine göre konumlandırmak önemlidir.  
  
 Aşağıdaki koşullar doğru olduğunda özel durumları yakalamanız gerekir:  
  
- Özel durum neden atılmış olabilir iyi bir anlayışa sahip ve bir nesne yakalamak zaman yeni bir dosya adı <xref:System.IO.FileNotFoundException> girmek için kullanıcı isteyen gibi belirli bir kurtarma uygulayabilirsiniz.  
  
- Yeni, daha özel bir özel durum oluşturabilir ve atabilirsiniz.  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- Ek işleme için geçirmeden önce bir özel durum kısmen işlemek istiyorsunuz. Aşağıdaki örnekte, `catch` özel durumu yeniden atmadan önce hata günlüğüne giriş eklemek için bir blok kullanılır.  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Son Bloklar  
 Blok, `finally` bir `try` blokta gerçekleştirilen eylemleri temizlemenizi sağlar. Varsa, `finally` blok, `try` blok ve eşleşen `catch` blok sonra, son yürütür. Bir `finally` özel durum atılıp atılmadığına veya özel `catch` durum türüyle eşleşen bir blok bulunup bulunmadığına bakılmaksızın, bir blok her zaman çalışır.  
  
 Blok, `finally` nesneleri sonuçlandırmak için çalışma zamanında çöp toplayıcısını beklemeden dosya akışları, veritabanı bağlantıları ve grafik işletmeleri gibi kaynakları serbest bırakmak için kullanılabilir. Daha fazla bilgi için [Bildirim'i kullanma](../../language-reference/keywords/using-statement.md) bilgisine bakın.  
  
 Aşağıdaki örnekte, `finally` blok, `try` blokta açılan bir dosyayı kapatmak için kullanılır. Dosya kapanmadan önce dosya tanıtıcısının durumunun denetlenir olduğuna dikkat edin. Blok dosyayı açamıyorsa, dosya tutamacı `null` yine `finally` de değere sahiptir ve blok dosyayı kapatmaya çalışmaz. `try` Alternatif olarak, dosya `try` blokta başarıyla açılırsa, `finally` blok açık dosyayı kapatır.  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Özel Durumlar](~/_csharplang/spec/exceptions.md) ve [Try deyimine](~/_csharplang/spec/statements.md#the-try-statement) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Referans](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum Kullanımı](./index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [Ekstresi'ni kullanma](../../language-reference/keywords/using-statement.md)
