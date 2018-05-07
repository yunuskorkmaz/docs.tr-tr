---
title: Özel Durum İşleme (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], handling
ms.assetid: b4e4ecf2-b907-4e58-891f-2563762258e9
ms.openlocfilehash: bbe9db48ab5cc1313c18fce66312f4334b40b9c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="exception-handling-c-programming-guide"></a>Özel Durum İşleme (C# Programlama Kılavuzu)
A [deneyin](../../../csharp/language-reference/keywords/try-catch.md) blok C# programcıları için bir özel durum tarafından etkilenebilir bölüm kod tarafından kullanılır. İlişkili [catch](../../../csharp/language-reference/keywords/try-catch.md) blokları, sonuçta elde edilen özel durumları işlemek için kullanılır. A [son](../../../csharp/language-reference/keywords/try-finally.md) blok olsun veya olmasın bir özel durum bağımsız olarak çalıştırma kodunu içerir `try` içinde ayrılan kaynakları serbest bırakma gibi blok `try` bloğu. A `try` blok gerektiren bir veya daha fazla ilişkili `catch` blokları, veya bir `finally` engelleme veya her ikisi de.  
  
 Aşağıdaki örneklerde gösterildiği bir `try-catch` deyimi, bir `try-finally` deyimi ve bir `try-catch-finally` deyimi.  
  
 [!code-csharp[csProgGuideExceptions#6](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_1.cs)]  
  
 [!code-csharp[csProgGuideExceptions#7](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_2.cs)]  
  
 [!code-csharp[csProgGuideExceptions#8](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_3.cs)]  
  
 A `try` olmadan engelleme bir `catch` veya `finally` blok derleyici hatası neden olur.  
  
## <a name="catch-blocks"></a>Catch blokları  
 A `catch` blok yakalamak için özel durum türünü belirtebilirsiniz. Tür belirtimi adlı bir *özel durum filtresi*. Özel durum türü türetilmiş <xref:System.Exception>. Genel olarak, belirtmeyin <xref:System.Exception> özel durum filtre olarak ya da bir durum içinde tüm özel durumları işleme bilmiyorsanız `try` engelleme veya dahil ettiyseniz bir [throw](../../../csharp/language-reference/keywords/throw.md) deyimi, sonunda`catch`bloğu.  
  
 Birden çok `catch` farklı özel durum filtreleri bloklarla zincirleme yapılabilir birlikte. `catch` Blokları değerlendirilir üstten alta kodunuzu, ancak yalnızca bir `catch` blok oluşturulan her bir özel durum için gerçekleştirilir. İlk `catch` türünü tam ya da oluşturulan özel durum, bir taban sınıf belirtir blok gerçekleştirilir. Yoksa `catch` blok belirtir eşleşen bir özel durum filtresi bir `catch` bir filtre yok blok seçilirse, bir deyimde mevcut değilse. Konumlandırmak önemlidir `catch` en (diğer bir deyişle, en çok türetilen) özel durum bloklarla türleri ilk.  
  
 Aşağıdaki koşullar doğru olduğunda özel durumlarını yakalama:  
  
-   Bir iyi, özel durum ve kullanıcıdan, catch zaman yeni bir dosya adı girin gibi belirli bir kurtarma, uygulayabilirsiniz neden anlama sahip bir <xref:System.IO.FileNotFoundException> nesnesi.  
  
-   Oluşturun ve yeni, daha belirli bir özel durum.  
  
     [!code-csharp[csProgGuideExceptions#9](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_4.cs)]  
  
-   Kısmen, ek işleme için'a geçirmeden önce özel bir durumu işlemek istediğiniz. Aşağıdaki örnekte, bir `catch` bloğu, özel durum yeniden atmadan önce bir hata günlüğü için bir giriş eklemek için kullanılır.  
  
     [!code-csharp[csProgGuideExceptions#10](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_5.cs)]  
  
## <a name="finally-blocks"></a>Finally blokları  
 A `finally` bloğu içinde gerçekleştirilen eylemler temizlemek etkinleştirir bir `try` bloğu. Varsa, `finally` blok sonra sonuncu yürütür `try` bloğu ve herhangi bir eşleşen `catch` bloğu. A `finally` engelleme her zaman çalışır, bağımsız olarak, bir özel durum veya bir `catch` özel durum türü eşleşen blok bulundu.  
  
 `finally` Bloğu, dosya akışlar, veritabanı bağlantıları gibi kaynakları serbest bırakmak için kullanılabilir ve grafik işleme atık toplayıcı çalışma zamanında nesneleri sonlandırmaya beklemeden. Bkz: [deyimiyle](../../../csharp/language-reference/keywords/using-statement.md) daha fazla bilgi için.  
  
 Aşağıdaki örnekte, `finally` bloğu içinde açılmış bir dosyayı kapatma için kullanılan `try` bloğu. Dosya kapatılmadan önce dosya tanıtıcısı durumunu işaretli olduğuna dikkat edin. Varsa `try` blok dosyayı açamıyor, dosya tanıtıcısı hala değerine sahip `null` ve `finally` blok kapatmak deneyin değil. Alternatif olarak, dosya başarıyla açılırsa `try` bloğu `finally` blok açık dosyayı kapatır.  
  
 [!code-csharp[csProgGuideExceptions#11](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/exception-handling_6.cs)]  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# başvurusu](../../../csharp/language-reference/index.md)  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özel Durumlar ve Özel Durum İşleme](../../../csharp/programming-guide/exceptions/index.md)  
 [try-catch](../../../csharp/language-reference/keywords/try-catch.md)  
 [try-finally](../../../csharp/language-reference/keywords/try-finally.md)  
 [try-catch-finally](../../../csharp/language-reference/keywords/try-catch-finally.md)  
 [using Deyimi](../../../csharp/language-reference/keywords/using-statement.md)
