---
title: Özel Durumlar Oluşturma ve Atma - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: f775a0917560a219f24329adcb1542f605d47dc2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712305"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Özel Durumlar Oluşturma ve Atma (C# Programlama Kılavuzu)
Özel durumlar, programı çalıştırırken bir hata oluştuğunu belirtmek için kullanılır. Bir hatayı açıklayan özel durum nesneleri oluşturulur ve [sonra atma](../../language-reference/keywords/throw.md) anahtar sözcüğüyle *birlikte atılır.* Çalışma süresi sonra en uyumlu özel durum işleyicisi arar.  
  
 Programcılar, aşağıdaki koşullardan biri veya birkaçı doğru olduğunda özel durumlar sunmalıdır:  
  
- Yöntem tanımlanan işlevselliğini tamamlayamıyor.  
  
     Örneğin, bir yöntemin parametresi geçersiz bir değere sahipse:  
  
     [!code-csharp[csProgGuideExceptions#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#12)]  
  
- Nesne durumuna göre nesneye uygunsuz bir çağrı yapılır.  
  
     Bir örnek, salt okunur dosyaya yazmaya çalışıyor olabilir. Nesne durumunun bir işleme izin vermediği durumlarda, bu sınıfın türemesine dayalı bir örnek <xref:System.InvalidOperationException> veya nesne atın. Bu, bir <xref:System.InvalidOperationException> nesne atan bir yönteme örnektir:  
  
     [!code-csharp[csProgGuideExceptions#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#13)]  
  
- Bir yöntemiçin bir bağımsız değişken bir özel durum neden olduğunda.  
  
     Bu durumda, özgün özel durum yakalanmalı ve bir <xref:System.ArgumentException> örnek oluşturulmalıdır. Özgün özel <xref:System.ArgumentException> <xref:System.Exception.InnerException%2A> durum, parametre olarak oluşturucuya geçirilmelidir:  
  
     [!code-csharp[csProgGuideExceptions#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#14)]  
  
 Özel durumlar adlı <xref:System.Exception.StackTrace%2A>bir özellik içerir. Bu dize, her yöntem için özel durum atıldığı dosya adı ve satır numarasıyla birlikte geçerli çağrı yığınındaki yöntemlerin adını içerir. Bir <xref:System.Exception.StackTrace%2A> `throw` nesne, deyim in den itibaren ortak dil çalışma süresi (CLR) tarafından otomatik olarak oluşturulur, böylece yığın izlemenin başlaması gereken noktadan özel durumlar atılmalıdır.  
  
 Tüm özel durumlar adlı <xref:System.Exception.Message%2A>bir özellik içerir. Bu dize, özel durum nedenini açıklamak için ayarlanmalıdır. Güvenlik açısından hassas olan bilgilerin ileti metnine konulmaması gerektiğini unutmayın. Buna ek <xref:System.Exception.Message%2A> <xref:System.ArgumentException> olarak, özel <xref:System.ArgumentException.ParamName%2A> durum atılmasına neden olan bağımsız değişkenin adına ayarlanmalıdır adlı bir özellik içerir. Bir özellik ayarlayıcısı durumunda, <xref:System.ArgumentException.ParamName%2A> 'ye `value`ayarlanmalıdır.  
  
 Genel ve korumalı yöntemler, amaçlanan işlevlerini tamamlayamadıkları zaman özel durumlar atmalıdır. Atılan özel durum sınıfı, hata koşullarına uyan kullanılabilir en özel özel özel durum olmalıdır. Bu özel durumlar sınıf işlevselliğinin bir parçası olarak belgelenmeli ve özgün sınıfa türetilen sınıflar veya güncelleştirmeler geriye dönük uyumluluk için aynı davranışı korumalıdır.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>İstisna Atarken Kaçınılması Gerekenler  
 Aşağıdaki liste, özel durumlar atarken kaçınılması gereken uygulamaları tanımlar:  
  
- Özel durumlar, olağan yürütmenin bir parçası olarak bir programın akışını değiştirmek için kullanılmamalıdır. Özel durumlar yalnızca hata koşullarını bildirmek ve işlemek için kullanılmalıdır.  
  
- Özel durumlar, atılmak yerine iade değeri veya parametre olarak döndürülmemelidir.  
  
- Kendi kaynak <xref:System.Exception?displayProperty=nameWithType> <xref:System.SystemException?displayProperty=nameWithType>kodunuzdan kasıtlı olarak , veya <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> kasıtlı olarak atmayın. <xref:System.NullReferenceException?displayProperty=nameWithType>  
  
- Hata ayıklama modunda atılabilir, ancak serbest bırakma modunda oluşturulabilecek özel durumlar oluşturmayın. Geliştirme aşamasında çalışma zamanı hatalarını tanımlamak için Hata Ayıklama İddiası'nı kullanın.  
  
## <a name="defining-exception-classes"></a>Özel Durum Sınıflarını Tanımlama  
 Programlar <xref:System> ad alanına önceden tanımlanmış bir özel durum sınıfı atabilir (daha önce belirtilmiş olan <xref:System.Exception>durumlar hariç) veya 'den türeerek kendi özel durum sınıflarını oluşturabilirler. Türemiş sınıflar en az dört oluşturucu tanımlamalıdır: bir parametresiz oluşturucu, ileti özelliğini ayarlayan ve hem özellikleri <xref:System.Exception.Message%2A> hem de <xref:System.Exception.InnerException%2A> özellikleri belirleyen bir tane. Dördüncü oluşturucu özel durumu serihale getirmek için kullanılır. Yeni özel durum sınıfları serileştirilebilir olmalıdır. Örnek:  
  
 [!code-csharp[csProgGuideExceptions#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#15)]  
  
 Yeni özellikler yalnızca sağladıkları veriler özel durumu çözmek için yararlı olduğunda özel durum sınıfına eklenmelidir. Türemiş özel durum sınıfına `ToString()` yeni özellikler eklenirse, eklenen bilgileri döndürmek için geçersiz kılınması gerekir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için [C# Dil Belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Özel Durumlar](~/_csharplang/spec/exceptions.md) ve [atma deyimine](~/_csharplang/spec/statements.md#the-throw-statement) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum Kullanımı](./index.md)
- [Özel Durum Hiyerarşisi](../../../standard/exceptions/index.md)
- [Özel Durum Taşıma](./exception-handling.md)
