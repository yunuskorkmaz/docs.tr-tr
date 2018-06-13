---
title: Özel Durumlar Oluşturma ve Atma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: 91676830d88ddee79c72211ab43b7be32fa8724e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336062"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Özel Durumlar Oluşturma ve Atma (C# Programlama Kılavuzu)
Özel durumlar programı çalıştırılırken bir hata oluştu belirtmek için kullanılır. Bir hata açıklayan özel durum nesneleri oluşturulur ve ardından *durum* ile [throw](../../../csharp/language-reference/keywords/throw.md) anahtar sözcüğü. Çalışma zamanı sonra en uyumlu özel durum işleyici arar.  
  
 Özel durumlar varsa programcıları oluşturması gerekir ya da daha aşağıdaki koşullardan biri doğru olduğunda:  
  
-   Yöntemi, tanımlanmış işlevselliğini tamamlayamıyor.  
  
     Örneğin, bir yöntem parametresi geçersiz bir değer varsa:  
  
     [!code-csharp[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   Nesne durumuna bağlı bir nesne için uygun olmayan bir çağrı yapılır.  
  
     Bir salt okunur dosyaya yazmak bir örnek çalışıyor olabilir. Örneği burada bir nesne durumu izin vermediğinden bir işlem durumlarda throw <xref:System.InvalidOperationException> ya da bu sınıf bir türevi dayalı bir nesne. Bu bir örnektir oluşturur bir yöntemin bir <xref:System.InvalidOperationException> nesnesi:  
  
     [!code-csharp[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   Ne zaman bir yöntemi için bağımsız değişken bir özel durum oluşur.  
  
     Bu durumda, orijinal özel durumu yakalandı ve bir <xref:System.ArgumentException> örneği oluşturulabilir. Orijinal özel durumu oluşturucusuna geçirilen <xref:System.ArgumentException> olarak <xref:System.Exception.InnerException%2A> parametre:  
  
     [!code-csharp[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 Özel durumlar adlı bir özellik içeren <xref:System.Exception.StackTrace%2A>. Bu dize, burada her yöntemi için özel durum oluştu dosya adı ve satır numarası ile birlikte geçerli çağrı yığınında yöntemler adını içerir. A <xref:System.Exception.StackTrace%2A> nesnesi tarafından oluşturulur otomatik olarak noktasından ortak dil çalışma zamanı (CLR) `throw` deyimi, böylece yığın izlemesi burada başlamalıdır noktasından durumlar gerekir.  
  
 Tüm özel durumları adlı bir özellik içeren <xref:System.Exception.Message%2A>. Bu dize, özel durumun nedeni açıklamak için ayarlanmalıdır. Güvenlik için hassas bilgileri metinde sokulmalıdır değil olduğunu unutmayın. Ek olarak <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> adlı bir özellik içeriyor <xref:System.ArgumentException.ParamName%2A> oluşturulmasına özel duruma neden bağımsız değişken adına ayarlanmalıdır. Özellik ayarlayıcısı durumunda <xref:System.ArgumentException.ParamName%2A> ayarlanmalı `value`.  
  
 Hedeflenen işlevleriyle tamamlayamıyor her ortak ve korumalı yöntemleri üyeleri özel durumlar oluşturması gerekir. Oluşturulan özel durum sınıfı en belirli özel durum hata koşulları uygun kullanılabilir olması gerekir. Bu özel durumlar sınıf işlevselliğinin bir parçası olarak belgelenen ve türetilmiş sınıfları veya aynı davranışı geriye dönük uyumluluk için özgün sınıfı güncelleştirmeleri korurlar.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Özel durumları atma zaman kaçının gerekenler  
 Aşağıdaki listede özel durumları atma zaman Kaçınılacak yöntemler tanımlanmaktadır:  
  
-   Özel durumlar sıradan yürütme bir parçası olarak bir programı akışını değiştirmek için kullanılmamalıdır. Özel durumlar, yalnızca rapor ve hata koşullarını işlemek için kullanılmalıdır.  
  
-   Özel durumlar bir dönüş değeri veya oluşturulan yerine parametresi olarak döndürülmelidir değil.  
  
-   Değil throw <xref:System.Exception?displayProperty=nameWithType>, <xref:System.SystemException?displayProperty=nameWithType>, <xref:System.NullReferenceException?displayProperty=nameWithType>, veya <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> kendi kaynak koddan kasıtlı olarak.  
  
-   Hata ayıklama modunda oluşturulur ancak Toolkit değil, özel durumlar oluşturmayın. Geliştirme aşaması sırasında çalışma zamanı hataları belirlemek için hata ayıklama Assert kullanın.  
  
## <a name="defining-exception-classes"></a>Özel durum sınıfları tanımlama  
 Programlar throw önceden tanımlanmış özel durum sınıfı <xref:System> (daha önce belirtilenler dışında), ad alanı veya kendi özel durum sınıfları türetme tarafından oluşturmak <xref:System.Exception>. Türetilen sınıflar en az dört oluşturucular tanımlamanız gerekir: bir varsayılan oluşturucu, ileti özelliğini ayarlayan, diğeri her ikisi de ayarlayan <xref:System.Exception.Message%2A> ve <xref:System.Exception.InnerException%2A> özellikleri. Dördüncü Oluşturucusu özel durum seri hale getirmek için kullanılır. Yeni özel durum sınıfları Serileştirilebilir olmalıdır. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 Sağladıkları veriler özel çözme için yararlı olduğunda yeni özellikler yalnızca özel durum sınıfına eklenmesi gerekir. Yeni özellikleri türetilmiş özel durum sınıfına eklediyseniz `ToString()` eklenen bilgileri döndürmek için geçersiz kılınmalıdır.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
 [Özel Durumlar ve Özel Durum İşleme](../../../csharp/programming-guide/exceptions/index.md)  
 [Özel durum hiyerarşisi](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)  
 [Özel Durum İşleme](../../../csharp/programming-guide/exceptions/exception-handling.md)
