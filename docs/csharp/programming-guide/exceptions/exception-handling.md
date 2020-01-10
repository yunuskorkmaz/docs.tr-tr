---
title: Özel durum Işleme C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: ee1e5bd15183dad9ffe97824f9b194668e9d3b17
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705307"
---
# <a name="exception-handling-c-programming-guide"></a>Özel Durum İşleme (C# Programlama Kılavuzu)
[TRY](../../language-reference/keywords/try-catch.md) bloğu, programcılar tarafından C# bir özel durumdan etkilenebilecek kodu bölümlemek için kullanılır. İlişkili [catch](../../language-reference/keywords/try-catch.md) blokları, ortaya çıkan özel durumları işlemek için kullanılır. [Finally](../../language-reference/keywords/try-finally.md) bloğu, `try` bloğunda ayrılan kaynakları serbest bırakma gibi `try` bloğunda bir özel durumun oluşturulup oluşturulmayacağını bakılmaksızın çalıştırılan kodu içerir. `try` bir blok, bir veya daha fazla ilişkili `catch` bloğunu veya `finally` bloğunu veya her ikisini de gerektirir.  
  
 Aşağıdaki örneklerde bir `try-catch` ifadeyi, bir `try-finally` ifadesini ve `try-catch-finally` ifadesini gösterir.  
  
 [!code-csharp[csProgGuideExceptions#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#6)]  
  
 [!code-csharp[csProgGuideExceptions#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#7)]  
  
 [!code-csharp[csProgGuideExceptions#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#8)]  
  
 `catch` veya `finally` bloğu olmayan `try` bloğu bir derleyici hatasına neden olur.  
  
## <a name="catch-blocks"></a>Catch blokları  
 `catch` bloğu, yakalamak için özel durum türünü belirtebilir. Tür belirtimine *özel durum filtresi*denir. Özel durum türü <xref:System.Exception>türetilmelidir. Genel olarak, `try` bloğunda oluşturulan tüm özel durumları nasıl işleyebileceğinizi veya `catch` blobunun sonuna bir [throw](../../language-reference/keywords/throw.md) bildirisi eklemiş olmanız durumunda özel durum filtresi olarak <xref:System.Exception> belirtmeyin.  
  
 Farklı özel durum filtrelerine sahip birden çok `catch` bloğu birlikte zincirlenebilir. `catch` blokları kodunuzda yukarıdan aşağıya değerlendirilir, ancak oluşturulan her özel durum için yalnızca bir `catch` bloğu yürütülür. Oluşturulan özel durumun tam türünü veya temel sınıfını belirten ilk `catch` bloğu yürütülür. `catch` bloğu eşleşen bir özel durum filtresi belirtiyorsa, deyimde bir filtre varsa, filtresi olmayan bir `catch` bloğu seçilir. En belirli (yani, en türetilmiş) özel durum türleri `catch` blokları konumlandırmak önemlidir.  
  
 Aşağıdaki koşullar doğru olduğunda özel durumları yakalamalı:  
  
- Özel durumun neden oluşturulması gerektiği konusunda iyi bir fikir sahibi olabilirsiniz ve bir <xref:System.IO.FileNotFoundException> nesnesi yakalarsanız kullanıcıdan yeni bir dosya adı girmesini isteme gibi belirli bir kurtarma uygulayabilirsiniz.  
  
- Yeni, daha özel bir özel durum oluşturabilir ve silebilirsiniz.  
  
     [!code-csharp[csProgGuideExceptions#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#9)]  
  
- Ek işleme için geçirmeden önce bir özel durumu kısmen işlemek istiyorsunuz. Aşağıdaki örnekte, özel durumu yeniden oluşturmadan önce bir hata günlüğüne giriş eklemek için bir `catch` bloğu kullanılır.  
  
     [!code-csharp[csProgGuideExceptions#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#10)]  
  
## <a name="finally-blocks"></a>Finally blokları  
 `finally` bir blok, bir `try` bloğunda gerçekleştirilen eylemleri temizlemenize olanak sağlar. Varsa, `try` bloğundan ve eşleşen `catch` bloğundan sonra `finally` bloğu son yürütülür. Bir özel durumun oluşturulup oluşturulmayacağını veya özel durum türüyle eşleşen bir `catch` bloğunun bulunup bulunamadığına bakılmaksızın `finally` bloğu her zaman çalışır.  
  
 `finally` bloğu, çalışma zamanındaki çöp toplayıcısının nesneleri son haline getirilmeksizin dosya akışları, veritabanı bağlantıları ve grafik tutamaçları gibi kaynakları serbest bırakmak için kullanılabilir. Daha fazla bilgi için bkz. [using deyimleri](../../language-reference/keywords/using-statement.md) .  
  
 Aşağıdaki örnekte, `finally` bloğu `try` bloğunda açılan bir dosyayı kapatmak için kullanılır. Dosya tutamacı durumunun, dosya kapatılmadan önce denetlendiğine dikkat edin. `try` bloğu dosyayı açmayabilir, dosya tanıtıcısı yine de `null` değerine sahiptir ve `finally` bloğu bunu kapatmayı denemez. Alternatif olarak, `try` bloğunda dosya başarılı bir şekilde açılırsa, `finally` bloğu açık dosyayı kapatır.  
  
 [!code-csharp[csProgGuideExceptions#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#11)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Exceptions](~/_csharplang/spec/exceptions.md) ve [TRY deyimleri](~/_csharplang/spec/statements.md#the-try-statement) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C#Başvurunun](../../language-reference/index.md)
- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
- [try-catch](../../language-reference/keywords/try-catch.md)
- [try-finally](../../language-reference/keywords/try-finally.md)
- [try-catch-finally](../../language-reference/keywords/try-catch-finally.md)
- [using Deyimi](../../language-reference/keywords/using-statement.md)
