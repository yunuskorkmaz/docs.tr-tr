---
title: Özel durumlar kullanma C# -Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 4012027dc1a9bd2543d0a4195360e5f7e0586fe1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705268"
---
# <a name="using-exceptions-c-programming-guide"></a>Özel Durumlar Kullanma (C# Programlama Kılavuzu)
İçinde C#, çalışma zamanında programdaki hatalar, özel durumlar adlı bir mekanizma kullanılarak program aracılığıyla dağıtılır. Özel durumlar, hata ile karşılaştığında ve hatayı düzeltebileceğiniz kodla yakalanan kodla oluşturulur. Özel durumlar .NET Framework ortak dil çalışma zamanı (CLR) veya bir programdaki kodla oluşturulabilir. Bir özel durum oluşturulduktan sonra, özel durum için `catch` bir bildirim bulunana kadar çağrı yığınını yayar. Yakalanamayan özel durumlar, bir iletişim kutusu görüntüleyen sistem tarafından sunulan genel bir özel durum işleyicisi tarafından işlenir.  
  
 Özel durumlar <xref:System.Exception>türetilmiş sınıflar tarafından temsil edilir. Bu sınıf, özel durum türünü tanımlar ve özel durumla ilgili ayrıntıları içeren özellikleri içerir. Özel durum oluşturmak, özel durum türetilmiş sınıfın bir örneğini oluşturmayı, isteğe bağlı olarak özel durumun özelliklerini yapılandırmayı ve sonra `throw` anahtar sözcüğünü kullanarak nesneyi oluşturmayı içerir. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Bir özel durum oluşturulduktan sonra, çalışma zamanı bir `try` bloğu içinde olup olmadığını görmek için geçerli ifadeyi denetler. Eğer ise, `try` bloğunun ilişkili tüm `catch` blokları özel durumu yakalayıp yakalayamayacağını görmek için denetlenir. `Catch` blokları genellikle özel durum türlerini belirtir; `catch` bloğunun türü özel durumla aynı türde veya özel durumun temel bir sınıfı ise, `catch` bloğu yöntemi işleyebilir. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Bir özel durum oluşturan ifade `try` bir blok içinde değilse veya kendisini kapsayan `try` bloğunun eşleşen `catch` bloğu yoksa, çalışma zamanı `try` bir deyimin ve `catch` blokların çağırma yöntemini denetler. Çalışma zamanı, arama yığınını devam ettirir ve uyumlu bir `catch` bloğunu arar. `catch` bloğu bulduktan ve yürütüldükten sonra, denetim bir sonraki ifadeye bu `catch` bloğundan sonra geçirilir.  
  
 `try` bir bildirimde birden fazla `catch` bloğu bulunabilir. Özel durumu işleyebilen ilk `catch` deyimleri yürütülür; uyumlu olsalar bile, aşağıdaki `catch` deyimleri yok sayılır. Bu nedenle, catch blokları her zaman en belirli (veya en çok türetilen) en azından belirli bir şekilde sıralanmalıdır. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 `catch` bloğu yürütülmeden önce, çalışma zamanı `finally` blokları denetler. `Finally` blokları, programcı 'nin, iptal edilmiş bir `try` bloğundan veya herhangi bir dış kaynağın (grafik tutamaçları, veritabanı bağlantıları veya dosya akışları gibi), çalışma zamanındaki çöp toplayıcısının nesneleri sonlandırmasına gerek kalmadan temizlenmesini sağlar. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 `WriteByte()` bir özel durum oluştursa, dosyayı yeniden açmaya çalışan ikinci `try` bloğundaki kod, `file.Close()` çağrılmazlarsa ve dosya kilitli kalırsa başarısız olur. Bir özel durum oluşsa bile `finally` blokları yürütüldüğü için, önceki örnekteki `finally` bloğu dosyanın düzgün şekilde kapatılmasını sağlar ve bir hatadan kaçınmaya yardımcı olur.  
  
 Bir özel durum oluşturulduktan sonra çağrı yığınında uyumlu bir `catch` bloğu bulunmazsa, üç durumdan biri oluşur:  
  
- Özel durum bir Sonlandırıcı içindeyse Sonlandırıcı iptal edilir ve varsa taban sonlandırıcısı çağırılır.  
  
- Çağrı yığını statik bir Oluşturucu veya statik bir alan başlatıcısı içeriyorsa, yeni özel durumun <xref:System.Exception.InnerException%2A> özelliğine atanan özgün özel durum ile bir <xref:System.TypeInitializationException> oluşturulur.  
  
- İş parçacığının başlangıcına ulaşıldığında, iş parçacığı sonlandırılır.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
