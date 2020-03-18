---
title: Özel Durumları Kullanma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 4012027dc1a9bd2543d0a4195360e5f7e0586fe1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75705268"
---
# <a name="using-exceptions-c-programming-guide"></a>Özel Durumlar Kullanma (C# Programlama Kılavuzu)
C#'da, programdaki hatalar çalışma zamanında özel durumlar adı verilen bir mekanizma kullanılarak program aracılığıyla yayılır. Özel durumlar, bir hatayla karşılaşan ve hatayı düzeltebilecek kod tarafından yakalanan kod tarafından atılır. Özel durumlar .NET Framework ortak dil çalışma zamanı (CLR) veya bir programdaki kod tarafından atılabilir. Bir özel durum atıldığında, özel durum `catch` bildirimi bulunana kadar çağrı yığınını yayır. Yakalanmayan özel durumlar, iletişim kutusu görüntüleyen sistem tarafından sağlanan genel bir özel durum işleyicisi tarafından işlenir.  
  
 Özel durumlar, 'den <xref:System.Exception>türetilen sınıflar tarafından temsil edilir. Bu sınıf özel durum türünü tanımlar ve özel durum la ilgili ayrıntıları olan özellikleri içerir. Özel durum atma, özel durum türetilmiş bir sınıfın bir örneğini oluşturmayı, isteğe `throw` bağlı olarak özel durum özelliklerini yapılandırmayı ve ardından anahtar kelimeyi kullanarak nesneyi atmayı içerir. Örnek:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Bir özel durum atıldıktan sonra, çalışma zamanı bir `try` blok içinde olup olmadığını görmek için geçerli deyimi denetler. Bu ysa, `catch` `try` özel durumu yakalayıp yakalayamayacaklarını görmek için blokla ilişkili bloklar denetlenir. `Catch`bloklar genellikle özel durum türlerini belirtir; `catch` bloğun türü özel durumla aynı türdeyse veya özel durum taban `catch` sınıfıysa, blok yöntemi işleyebilir. Örnek:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Özel durum atan deyim `try` bir blok içinde değilse `try` veya içine giren bloğun eşleşen `catch` bir bloğu yoksa, çalışma zamanı `try` deyimi `catch` ve blokları için arama yöntemini denetler. Çalışma süresi, uyumlu `catch` bir blok aramak için arama yığınına kadar devam ediyor. `catch` Blok bulunduktan ve yürütüldükten sonra, denetim `catch` bu bloktan sonra bir sonraki ifadeye geçirilir.  
  
 Bir `try` deyim birden `catch` fazla blok içerebilir. Özel `catch` durum işleyebilir ilk deyimi yürütülür; uyumlu `catch` olsalar bile aşağıdaki ifadeler göz ardı edilir. Bu nedenle, catch blokları her zaman en özel (veya en türetilmiş) en az özel sıralanmalıdır. Örnek:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Blok `catch` yürütülmeden önce, çalışma `finally` zamanı blokları denetler. `Finally`bloklar, programcının iptal edilmiş `try` bir bloktan arta kalan herhangi bir belirsiz durumu temizlemesini veya nesneleri sonuçlandırmak için çalışma zamanında çöp toplayıcısını beklemeden herhangi bir dış kaynağı (grafik tutamaçları, veritabanı bağlantıları veya dosya akışları gibi) serbest bırakmasına olanak tanır. Örnek:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 Bir `WriteByte()` özel durum atılırsa, `try` dosyayı yeniden açmaya çalışan ikinci `file.Close()` bloktaki kod çağrılmazsa başarısız olur ve dosya kilitli kalır. Bir `finally` özel durum atılsa bile `finally` bloklar yürütüldeğinden, önceki örnekteki blok dosyanın doğru şekilde kapatılmasına izin verir ve bir hatayı önlemeye yardımcı olur.  
  
 Özel durum `catch` atıldıktan sonra çağrı yığınında uyumlu bir blok bulunamazsa, üç şeyden biri oluşur:  
  
- İstisna bir sonlandırıcı içinde yse, sonlandırıcı iptal edilir ve varsa temel sonlandırıcı çağrılır.  
  
- Çağrı yığını statik bir oluşturucu veya statik alan baş <xref:System.TypeInitializationException> harflerini içeriyorsa, yeni <xref:System.Exception.InnerException%2A> özel durum özelliğine atanan özgün özel durumla birlikte bir atılmıştır.  
  
- İş parçacığının başlangıcına ulaşılırsa, iş parçacığı sonlandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum Kullanımı](./index.md)
