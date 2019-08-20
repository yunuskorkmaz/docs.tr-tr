---
title: Özel durumlar kullanma C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 8d0fe4b8c2ba3e64aa7ee34fc9d02b29bda5c017
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590175"
---
# <a name="using-exceptions-c-programming-guide"></a>Özel Durumlar Kullanma (C# Programlama Kılavuzu)
İçinde C#, çalışma zamanında programdaki hatalar, özel durumlar adlı bir mekanizma kullanılarak program aracılığıyla dağıtılır. Özel durumlar, hata ile karşılaştığında ve hatayı düzeltebileceğiniz kodla yakalanan kodla oluşturulur. Özel durumlar .NET Framework ortak dil çalışma zamanı (CLR) veya bir programdaki kodla oluşturulabilir. Bir özel durum oluşturulduktan sonra, özel durum için bir `catch` ifade bulunana kadar çağrı yığınını yayar. Yakalanamayan özel durumlar, bir iletişim kutusu görüntüleyen sistem tarafından sunulan genel bir özel durum işleyicisi tarafından işlenir.  
  
 Özel durumlar, öğesinden <xref:System.Exception>türetilmiş sınıflar tarafından temsil edilir. Bu sınıf, özel durum türünü tanımlar ve özel durumla ilgili ayrıntıları içeren özellikleri içerir. Özel durum oluşturmak, özel durum türetilmiş sınıfın bir örneğini oluşturmayı, isteğe bağlı olarak özel durumun özelliklerini yapılandırmayı ve sonra `throw` anahtar sözcüğünü kullanarak nesneyi oluşturmayı içerir. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Bir özel durum oluşturulduktan sonra, çalışma zamanı bir `try` blok içinde olup olmadığını görmek için geçerli ifadeyi denetler. Eğer ise, `try` bloğuyla `catch` ilişkili herhangi bir blok, özel durumu yakalayıp yakalayamayacağını görmek için denetlenir. `Catch`bloklar genellikle özel durum türlerini belirtir; `catch` bloğun türü özel durumla aynı türde veya özel durumun `catch` temel bir sınıfı ise, blok yöntemi işleyebilir. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Bir özel durum oluşturan ifade bir blok içinde `try` değilse veya `try` kendisini kapsayan blok eşleşen `catch` bir blok içindeyse, çalışma zamanı bir `try` deyimin ve `catch` blokların çağırma yöntemini denetler. Çalışma zamanı, arama yığınını devam ettirir ve uyumlu `catch` bir blok arar. Blok bulduktan ve yürütüldükten sonra, denetim bu `catch` blok sonrasında sonraki ifadeye geçirilir. `catch`  
  
 Bir `try` ifade, birden fazla `catch` blok içerebilir. Özel durumu `catch` işleyebilen ilk deyim yürütülür; uyumlu olsalar bile aşağıdaki `catch` deyimler yok sayılır. Bu nedenle, catch blokları her zaman en belirli (veya en çok türetilen) en azından belirli bir şekilde sıralanmalıdır. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Blok yürütülmeden önce, çalışma zamanı `finally` blokları denetler. `catch` `Finally`bloklar, programcı 'nin durdurulmuş `try` bir bloktan veya herhangi bir dış kaynağın (grafik tutamaçları, veritabanı bağlantıları veya dosya akışları gibi) çöp kutusu beklemeden serbest bırakılması için herhangi bir belirsiz durumu temizlemesini sağlar nesneleri sonlandırmak için çalışma zamanında toplayıcı. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 Bir özel durum, çağrılırsa dosyayı yeniden açmaya çalışan ikinci `try` bloktaki kod başarısız `file.Close()` olur ve dosya kilitli kalır. `WriteByte()` Bir özel durum oluşsa bile `finally` bloklaryürütüldüğüiçin,öncekiörnektekiblokdosyanındüzgünşekildekapatılmasınısağlarvebirhatadankaçınmayayardımcıolur.`finally`  
  
 Bir özel durum `catch` oluşturulduktan sonra çağrı yığınında uyumlu bir blok bulunmazsa, üç durumdan biri oluşur:  
  
- Özel durum bir Sonlandırıcı içindeyse Sonlandırıcı iptal edilir ve varsa taban sonlandırıcısı çağırılır.  
  
- Çağrı yığını statik bir Oluşturucu içeriyorsa veya bir statik alan Başlatıcısı <xref:System.TypeInitializationException> varsa, özgün özel durum yeni özel durumun <xref:System.Exception.InnerException%2A> özelliğine atanır.  
  
- İş parçacığının başlangıcına ulaşıldığında, iş parçacığı sonlandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
