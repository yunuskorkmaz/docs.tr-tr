---
title: Özel Durumlar Oluşturma ve Atma (C# Programlama Kılavuzu)
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: 2e792a230ccead5d9a73f9b78a83d57738c31085
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44260077"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Özel Durumlar Oluşturma ve Atma (C# Programlama Kılavuzu)
Özel durumlar programı çalıştırılırken bir hata oluştu belirtmek için kullanılır. Bir hata açıklayan özel durum nesneleri oluşturulur ve ardından *durum* ile [throw](../../../csharp/language-reference/keywords/throw.md) anahtar sözcüğü. Çalışma zamanı sonra en uyumlu özel durum işleyicisi arar.  
  
 Programcıların bir özel durum oluşturmamalıdır ya da daha aşağıdaki koşullardan biri doğru olduğunda:  
  
-   Yöntemi, tanımlanan işlevselliğini tamamlanamıyor.  
  
     Örneğin, bir yönteme parametre geçersiz bir değer varsa:  
  
     [!code-csharp[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]  
  
-   Nesne durumunu temel alan bir nesne için uygun bir çağrı yapılır.  
  
     Salt okunur bir dosyaya yazmak bir örnek çalışıyor olabilir. Örneği burada bir nesne durumu izin vermiyor bir işlem durumlarda, throw <xref:System.InvalidOperationException> veya üzerinde bu sınıfın bir türevi göre bir nesne. Bu bir örnektir oluşturan bir yöntemin bir <xref:System.InvalidOperationException> nesnesi:  
  
     [!code-csharp[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]  
  
-   Ne zaman bir yönteme bağımsız değişken, bir özel durum neden olur.  
  
     Bu durumda, özgün özel durum yakalandı ve bir <xref:System.ArgumentException> örneği oluşturulabilir. Özgün özel durum oluşturucusuna geçirilecek <xref:System.ArgumentException> olarak <xref:System.Exception.InnerException%2A> parametresi:  
  
     [!code-csharp[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]  
  
 Özel durumlar adlı bir özellik içeren <xref:System.Exception.StackTrace%2A>. Bu dize, burada her yöntem için özel durum oluştu dosya adı ve satır numarasını birlikte geçerli çağrı yığınında yöntemler adını içerir. A <xref:System.Exception.StackTrace%2A> nesne otomatik olarak tarafından oluşturulan noktasından ortak dil çalışma zamanı (CLR) `throw` deyimi, böylece özel durum yığın izlemesi nerede başlamalıdır noktasından oluşturulmalıdır.  
  
 Tüm özel durumları adlı bir özellik içeren <xref:System.Exception.Message%2A>. Bu dize, özel durumun nedenini açıklayacak şekilde ayarlanmalıdır. Güvenlik için hassas bilgileri metinde sokulmalıdır değil olduğunu unutmayın. Ek olarak <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> adlı bir özellik içeren <xref:System.ArgumentException.ParamName%2A> özel durum oluşturulmasına neden olan bir bağımsız değişken adına ayarlanmalıdır. Bir özellik ayarlayıcısı söz konusu olduğunda <xref:System.ArgumentException.ParamName%2A> ayarlanmalıdır `value`.  
  
 Bunlar, hedeflenen işlevlerini tamamlanamıyor her ortak ve korunan metotlara üyeleri özel durum oluşturmamalıdır. Hata koşulları, en uygun kullanılabilir en belirli özel durum harekete geçirilen özel durum sınıfı olmalıdır. Bu özel durum sınıfı işlevselliğe bir parçası olarak belgelenmelidir ve türetilmiş sınıflar veya orijinal sınıfta güncelleştirmeleri geriye dönük uyumluluk için aynı davranışı korurlar.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Özel durumları atma önlemek şeyler  
 Aşağıdaki liste, özel durumlar oluşturulduğunda Kaçınılacak yöntemler tanımlar:  
  
-   Özel durumlar, bir program akışını normal yürütmenin bir parçası olarak değiştirmek için kullanılmamalıdır. Özel durumlar, yalnızca rapor ve hata koşullarını işlemek için kullanılmalıdır.  
  
-   Özel durumlar bir dönüş değeri veya oluşturulan yerine parametre olarak döndürülmelidir değil.  
  
-   Throw değil <xref:System.Exception?displayProperty=nameWithType>, <xref:System.SystemException?displayProperty=nameWithType>, <xref:System.NullReferenceException?displayProperty=nameWithType>, veya <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> kendi kaynak kodundan kasıtlı olarak.  
  
-   Hata ayıklama modunda oluşturulur ancak yayınlama modunda değil, özel durumlar oluşturmayın. Çalışma zamanı hataları geliştirme aşamasında tanımlamak için hata ayıklama onaylama işlemi kullanın.  
  
## <a name="defining-exception-classes"></a>Özel durum sınıfları tanımlama  
 Programlar throw önceden tanımlanmış özel durum sınıfı <xref:System> (daha önce belirtilenler dışında), ad alanı veya kendi özel durum sınıfları türeterek oluşturma <xref:System.Exception>. En az dört oluşturucuları türetilmiş sınıfları tanımlamanız gerekir: bir varsayılan oluşturucu, ileti özelliği ayarlayan, diğeri her ikisi de ayarlayan <xref:System.Exception.Message%2A> ve <xref:System.Exception.InnerException%2A> özellikleri. Dördüncü Oluşturucu, özel durum seri hale getirmek için kullanılır. Yeni özel durum sınıfları seri hale getirilebilir olması. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]  
  
 Sağladıkları veriler özel durumu çözümlemek için yararlı olduğunda özel durum sınıfı için yeni özellikler yalnızca eklenmesi gerekir. Yeni özellikler türetilen özel durum sınıfına eklenirse `ToString()` ek bilgi döndürmek için geçersiz kılınmalıdır.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)  
- [Özel Durumlar ve Özel Durum İşleme](../../../csharp/programming-guide/exceptions/index.md)  
- [Özel durum hiyerarşisi](https://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b)  
- [Özel Durum İşleme](../../../csharp/programming-guide/exceptions/exception-handling.md)
