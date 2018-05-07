---
title: Özel Durumlar Kullanma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], about exception handling
- exceptions [C#], about exceptions
ms.assetid: 71472c62-320a-470a-97d2-67995180389d
ms.openlocfilehash: 43012ec1190117b1905b5e44010d5f57a1e543aa
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="using-exceptions-c-programming-guide"></a>Özel Durumlar Kullanma (C# Programlama Kılavuzu)
C# ' ta çalışma zamanında programında hataları program aracılığıyla özel durumlar olarak adlandırılan bir mekanizma kullanılarak dağıtılır. Özel durumlar hatayla karşılaştığında kodla oluşturulur ve hatayı düzeltmek için kullanabileceğiniz kodla yakalandı. .NET Framework ortak dil çalışma zamanı (CLR) veya kod içinde bir program tarafından özel durum. Bir özel durum oluşturulduktan sonra çağrı yığını kadar yukarı yayar bir `catch` özel durum bildirimi bulundu. Yakalanmayan Özel durumlar iletişim kutusu görüntüler sistem tarafından sağlanan bir genel özel durum işleyicisi tarafından işlenir.  
  
 Özel durumlar türetilmiş sınıflar tarafından gösterilen <xref:System.Exception>. Bu sınıf, özel durum türünü tanımlar ve özel durum ayrıntıları sahip özellikler içerir. Bir özel durum atma içerir bir özel durum türetilmiş sınıf örneği oluşturmayı, isteğe bağlı olarak özel özelliklerini yapılandırmak ve ardından kullanarak nesne atma `throw` anahtar sözcüğü. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#1](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_1.cs)]  
  
 Bir özel durum oluşturulduktan sonra çalışma zamanı geçerli deyimi içinde olup olmadığını denetler. bir `try` bloğu. Bunu varsa, `catch` ilişkili blokları `try` bloğu, bunlar özel durum catch olup olmadığını görmek için denetlenir. `Catch` blokları genellikle özel durum türleri belirtin; varsa türünü `catch` bloğu özel durum ya da bir taban sınıf özel durum, aynı türde `catch` blok yöntemi işleyebilir. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#2](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_2.cs)]  
  
 Aykırı deyimi içinde değilse, bir `try` blok veya `try` onu blok eşleşen sahip `catch` bloğu, çalışma zamanı için arama yöntemi olup olmadığına bakar bir `try` deyimi ve `catch` engeller. Çalışma zamanı için uyumlu bir arama Çağırma yığını yukarı devam `catch` bloğu. Sonra `catch` bloğu bulundu ve yürütülen, Denetim bundan sonra next deyimi iletilir `catch` bloğu.  
  
 A `try` deyimi birden fazla içerebilir `catch` bloğu. İlk `catch` özel durumu işleyebilecek deyimi yürütüldüğünde; tüm aşağıdaki `catch` deyimleri uyumlu olsalar bile, yok sayılır. Bu nedenle, catch blokları her zaman sıralı en belirli (veya en çok türetilen) az. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#3](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_3.cs)]  
  
 Önce `catch` blok yürütüldüğünde, çalışma zamanı denetler `finally` engeller. `Finally` blokları etkinleştirmek durdurulan kalabilir herhangi bir belirsiz durumu temizlemek Programcı `try` bloğu veya herhangi bir dış kaynağa (örneğin, grafik tanıtıcıları, veritabanı bağlantılarını veya dosya akışları) için çöp beklemeden serbest bırakmak için nesneleri sonlandırmaya Toplayıcı çalışma zamanında. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#4](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/using-exceptions_4.cs)]  
  
 Varsa `WriteByte()` ikinci kodda özel durum oluşturdu `try` , dosyayı yeniden dener blok başarısız olurdu `file.Close()` adlı değil ve dosyanın kilitli olarak kalır. Olduğundan `finally` blokları bir özel durum olsa bile, yürütülen `finally` önceki örnekte blok dosyanın doğru kapatılması sağlar ve yardımcı bir hata kaçının.  
  
 Hiçbir uyumlu değilse `catch` blok bulundu çağrı yığınındaki bir özel durum oluşturulduktan sonra üç şey biri oluşur:  
  
-   Özel durum sonlandırıcıyı içinde ise, sonlandırıcıyı iptal edilir ve temel sonlandırıcıyı varsa çağrılır.  
  
-   Çağrı yığını statik oluşturucu veya bir statik alan Başlatıcı içeriyorsa bir <xref:System.TypeInitializationException> atanan özgün özel durum <xref:System.Exception.InnerException%2A> yeni özel durum özelliği.  
  
-   İş parçacığının başlangıcını ulaştıysanız, iş parçacığı sonlandırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özel Durumlar ve Özel Durum İşleme](../../../csharp/programming-guide/exceptions/index.md)
