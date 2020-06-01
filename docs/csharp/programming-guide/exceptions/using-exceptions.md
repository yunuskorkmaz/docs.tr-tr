---
title: Özel durumlar kullanma-C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: a00259dfd5634ad9b9c951c3cd76da97afe5077d
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241701"
---
# <a name="use-exceptions-c-programming-guide"></a>Özel durumlar kullanma (C# Programlama Kılavuzu)

C# ' de, çalışma zamanında programdaki hatalar, özel durumlar adlı bir mekanizma kullanılarak program aracılığıyla dağıtılır. Özel durumlar, hata ile karşılaştığında ve hatayı düzeltebileceğiniz kodla yakalanan kodla oluşturulur. Özel durumlar .NET çalışma zamanı veya bir programdaki kodla oluşturulabilir. Bir özel durum oluşturulduktan sonra, özel durum için bir ifade bulunana kadar çağrı yığınını yayar `catch` . Yakalanamayan özel durumlar, bir iletişim kutusu görüntüleyen sistem tarafından sunulan genel bir özel durum işleyicisi tarafından işlenir.  
  
 Özel durumlar, öğesinden türetilmiş sınıflar tarafından temsil edilir <xref:System.Exception> . Bu sınıf, özel durum türünü tanımlar ve özel durumla ilgili ayrıntıları içeren özellikleri içerir. Özel durum oluşturmak, özel durum türetilmiş sınıfın bir örneğini oluşturmayı, isteğe bağlı olarak özel durumun özelliklerini yapılandırmayı ve sonra anahtar sözcüğünü kullanarak nesneyi oluşturmayı içerir `throw` . Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Bir özel durum oluşturulduktan sonra, çalışma zamanı bir blok içinde olup olmadığını görmek için geçerli ifadeyi denetler `try` . Eğer ise, `catch` bloğuyla ilişkili herhangi bir blok, `try` özel durumu yakalayıp yakalayamayacağını görmek için denetlenir. `Catch`bloklar genellikle özel durum türlerini belirtir; `catch`bloğun türü özel durumla aynı türde veya özel durumun temel bir sınıfı ise, `catch` blok yöntemi işleyebilir. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Bir özel durum oluşturan ifade bir blok içinde değilse `try` veya `try` kendisini kapsayan blok eşleşen bir `catch` blok içindeyse, çalışma zamanı bir `try` deyimin ve blokların çağırma yöntemini denetler `catch` . Çalışma zamanı, arama yığınını devam ettirir ve uyumlu bir blok arar `catch` . Blok bulduktan `catch` ve yürütüldükten sonra, denetim bu blok sonrasında sonraki ifadeye geçirilir `catch` .  
  
 Bir `try` ifade, birden fazla blok içerebilir `catch` . `catch`Özel durumu işleyebilen ilk deyim yürütülür; `catch` uyumlu olsalar bile aşağıdaki deyimler yok sayılır. Bu nedenle, catch blokları her zaman en belirli (veya en çok türetilen) en azından belirli bir şekilde sıralanmalıdır. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 `catch`Blok yürütülmeden önce, çalışma zamanı `finally` blokları denetler. `Finally`bloklar, programcı 'nin durdurulmuş bir `try` bloktan veya herhangi bir dış kaynağın (grafik tutamaçları, veritabanı bağlantıları veya dosya akışları gibi), çalışma zamanındaki çöp toplayıcısının nesneleri sonlandırmasına gerek kalmadan serbest bırakılmış olan herhangi bir durumu temizlemesini sağlar. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 `WriteByte()`Bir özel durum, `try` çağrılırsa dosyayı yeniden açmaya çalışan ikinci bloktaki kod başarısız olur `file.Close()` ve dosya kilitli kalır. `finally`Bir özel durum oluşsa bile bloklar yürütüldüğü `finally` için, önceki örnekteki blok dosyanın düzgün şekilde kapatılmasını sağlar ve bir hatadan kaçınmaya yardımcı olur.  
  
 `catch`Bir özel durum oluşturulduktan sonra çağrı yığınında uyumlu bir blok bulunmazsa, üç durumdan biri oluşur:  
  
- Özel durum bir Sonlandırıcı içindeyse Sonlandırıcı iptal edilir ve varsa taban sonlandırıcısı çağırılır.  
  
- Çağrı yığını statik bir Oluşturucu içeriyorsa veya bir statik alan başlatıcısı varsa, <xref:System.TypeInitializationException> özgün özel durum <xref:System.Exception.InnerException%2A> Yeni özel durumun özelliğine atanır.  
  
- İş parçacığının başlangıcına ulaşıldığında, iş parçacığı sonlandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
