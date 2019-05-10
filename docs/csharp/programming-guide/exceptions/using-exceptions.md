---
title: Özel durum - kullanarak C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 9ab6c5029518cbe5deb0f2c5a16c99992022d7a3
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64595475"
---
# <a name="using-exceptions-c-programming-guide"></a>Özel Durumlar Kullanma (C# Programlama Kılavuzu)
C# ' ta program çalışma zamanında hatalarını program aracılığıyla özel durumlar adlı bir mekanizmayı kullanarak yayılır. Özel durumlar hatayla karşılaştığında kod tarafından oluşturulur ve hatayı düzeltmek kodu tarafından yakalanan. Özel durumlar, .NET Framework ortak dil çalışma zamanı (CLR) veya bir program kodunda atılabilir. Bir özel durum sonra kadar çağrı yığınına yayan bir `catch` özel durum bildirimi bulundu. Yakalanmayan Özel durumların bir iletişim kutusu görüntüler sistem tarafından sağlanan bir genel özel durum işleyicisi tarafından işlenir.  
  
 Özel durumlar türetilmiş sınıflar tarafından temsil edilir <xref:System.Exception>. Bu sınıf, özel durumun türünü tanımlar ve özel durumun ayrıntılarını sahip özellikler içerir. Bir özel durum içeren bir özel durum türetilmiş sınıfın bir örneği oluşturma, isteğe bağlı olarak özel durumun özelliklerini yapılandırmak ve nesne kullanarak özel durum atma `throw` anahtar sözcüğü. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#1)]  
  
 Bir özel durum oluştuktan sonra çalışma zamanı içinde olup olmadığını görmek için geçerli deyim denetler. bir `try` blok. Bunu varsa, `catch` ilişkili blokları `try` blok istisnayı yakalamak mümkündür olup olmadığını görmek için denetlenir. `Catch` Bloklar, genellikle özel durum türlerini belirtin; varsa türünü `catch` bloğu özel durum ya da bir temel sınıf özel durumun, aynı türde `catch` blok yöntemi işleyebilir. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#2)]  
  
 Bir özel durum deyimi içinde değilse, bir `try` blok veya `try` kendisini kapsayan bir blok eşleşen yok `catch` blok, çalışma zamanı denetimleri için yöntemi çağrılırken bir `try` deyimi ve `catch` engeller. Çalışma zamanı için bir uyumlu arama çağrı yığınına devam `catch` blok. Sonra `catch` bloğu bulundu ve yürütüldü, Denetim, bundan sonra sonraki deyime geçirilir `catch` blok.  
  
 A `try` deyimi birden fazla içerebilir `catch` blok. İlk `catch` özel durumu işleyebilecek deyimi yürütülür; tüm aşağıdaki `catch` deyimleri uyumlu olsalar bile yok sayılır. Bu nedenle, catch blokları her zaman sıralı en belirli (veya en çok türetilen) az. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#3)]  
  
 Önce `catch` bloğu yürütülür için çalışma zamanı denetimleri `finally` engeller. `Finally` blokları etkinleştirme durdurulan kalabilir herhangi bir belirsiz durumu temizlemek Programcı `try` bloğu veya Çöp için beklemenize gerek kalmadan herhangi bir dış kaynağa (örneğin, grafik tanıtıcıları, veritabanı bağlantıları veya dosya akışları) serbest bırakmak için nesneleri sonlandırmak için toplayıcı çalışma zamanında. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#4)]  
  
 Varsa `WriteByte()` ikinci kod özel durum oluşturdu `try` , dosyayı yeniden dener blok başarısız olurdu `file.Close()` çağrılmaz, dosyanın kilitli kalır. Çünkü `finally` blokları, bir özel durum olsa bile, yürütülen `finally` blok önceki örnekte dosyanın doğru şekilde kapatılması sağlar ve kaçının bir hata yardımcı olur.  
  
 Hiçbir uyumlu değilse `catch` bloğu bulundu çağrı yığınındaki bir özel durum oluştuktan sonra üç şeylerden biri gerçekleşir:  
  
- Özel durum bir sonlandırıcı içinde ise, sonlandırıcı iptal edilir ve temel Sonlandırıcı varsa çağrılır.  
  
- Çağrı yığınını statik oluşturucu veya bir statik alan başlatıcısında içeriyorsa bir <xref:System.TypeInitializationException> atanmış olan özgün özel durum ile oluşan <xref:System.Exception.InnerException%2A> yeni özel durum özelliği.  
  
- İş parçacığının başlangıç ulaşılırsa, iş parçacığı sonlandırıldı.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [Özel Durumlar ve Özel Durum İşleme](../../../csharp/programming-guide/exceptions/index.md)
