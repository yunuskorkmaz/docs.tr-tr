---
title: Özel durumlar oluşturma ve atma C# -Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: dfc852722531c06f986f54221ad094b13496561f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/01/2019
ms.locfileid: "73417946"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Özel Durumlar Oluşturma ve Atma (C# Programlama Kılavuzu)
Özel durumlar, programı çalıştırırken bir hata oluştuğunu göstermek için kullanılır. Bir hatayı tanımlayan özel durum nesneleri oluşturulur ve [throw](../../language-reference/keywords/throw.md) anahtar *sözcüğüyle oluşturulur.* Çalışma zamanı, en uyumlu özel durum işleyicisini arar.  
  
 Aşağıdaki koşullardan biri veya daha fazlası doğru olduğunda programcılar özel durumlar atmalıdır:  
  
- Yöntem, tanımlı işlevini tamamlayamıyor.  
  
     Örneğin, bir yönteme ait bir parametre geçersiz bir değere sahipse:  
  
     [!code-csharp[csProgGuideExceptions#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#12)]  
  
- Nesne durumuna bağlı olarak bir nesneye uygun olmayan bir çağrı yapılır.  
  
     Bir örnek, salt okunurdur bir dosyaya yazmaya çalışıyor olabilir. Bir nesne durumunun bir işleme izin vermediği durumlarda, bu sınıfın bir türetmesi temelinde <xref:System.InvalidOperationException> veya bir nesnesi örneği oluşturun. Bu, <xref:System.InvalidOperationException> nesnesi oluşturan bir yönteme örnektir:  
  
     [!code-csharp[csProgGuideExceptions#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#13)]  
  
- Bir yöntemin bağımsız değişkeni bir özel duruma neden olur.  
  
     Bu durumda, özgün özel durumun yakalanmalı ve bir <xref:System.ArgumentException> örneğinin oluşturulması gerekir. Özgün özel durumun <xref:System.Exception.InnerException%2A> parametresi olarak <xref:System.ArgumentException> oluşturucusuna geçirilmesi gerekir:  
  
     [!code-csharp[csProgGuideExceptions#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#14)]  
  
 Özel durumlar <xref:System.Exception.StackTrace%2A>adlı bir özellik içerir. Bu dize, geçerli çağrı yığınındaki yöntemlerin adını, her yöntem için özel durumun oluşturulduğu dosya adı ve satır numarasıyla birlikte içerir. Bir <xref:System.Exception.StackTrace%2A> nesnesi, `throw` deyimin noktasındaki ortak dil çalışma zamanı (CLR) tarafından otomatik olarak oluşturulur. böylece, yığın izlemenin başlayacağı noktadan özel durumlar oluşturulmalıdır.  
  
 Tüm özel durumlar <xref:System.Exception.Message%2A>adlı bir özellik içerir. Bu dize, özel durumun nedenini açıklamak için ayarlanmalıdır. Güvenliğe duyarlı bilgilerin ileti metnine yerleştirilmemelidir. <xref:System.Exception.Message%2A>ek olarak, <xref:System.ArgumentException>, özel durumun oluşturulmasına neden olan bağımsız değişkenin adı olarak ayarlanması gereken <xref:System.ArgumentException.ParamName%2A> adlı bir özellik içerir. Özellik ayarlayıcısı durumunda, <xref:System.ArgumentException.ParamName%2A> `value`olarak ayarlanmalıdır.  
  
 Ortak ve korumalı Yöntemler, kendilerine amaçlanan işlevleri tamamlanamadığında özel durumlar atmalıdır. Oluşturulan özel durum sınıfı, hata koşullarına uyan en belirgin özel durum olmalıdır. Bu özel durumlar, sınıf işlevselliğinin bir parçası olarak belgelenmelidir ve özgün sınıftaki türetilmiş sınıflar veya güncelleştirmeler geriye dönük uyumluluk için aynı davranışı korurlar.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Özel durumlar oluştururken kaçınmak için gerekenler  
 Aşağıdaki liste, özel durumlar oluştururken kaçınmak için Yöntemler tanımlar:  
  
- Özel durumlar, bir programın akışını sıradan yürütmenin parçası olarak değiştirmek için kullanılmamalıdır. Özel durumlar yalnızca hata koşullarını raporlamak ve işlemek için kullanılmalıdır.  
  
- Özel durumlar, oluşturulması yerine dönüş değeri veya parametresi olarak döndürülmemelidir.  
  
- <xref:System.Exception?displayProperty=nameWithType>, <xref:System.SystemException?displayProperty=nameWithType>, <xref:System.NullReferenceException?displayProperty=nameWithType>veya <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> kasıtlı olarak kendi kaynak kodınızdan atamayın.  
  
- Hata ayıklama modunda, ancak serbest bırakma modunda oluşturulabilecek özel durumlar oluşturmayın. Geliştirme aşamasında çalışma zamanı hatalarını belirlemek için bunun yerine hata ayıklama onayı kullanın.  
  
## <a name="defining-exception-classes"></a>Özel durum sınıfları tanımlama  
 Programlar, <xref:System> ad alanında önceden tanımlanmış bir özel durum sınıfı oluşturabilir (daha önce belirtilen durumlar hariç) veya <xref:System.Exception>türeterek kendi özel durum sınıflarını oluşturabilir. Türetilmiş sınıflar en az dört Oluşturucu tanımlamalıdır: tek parametresiz bir Oluşturucu, ileti özelliğini ayarlayan diğeri ve hem <xref:System.Exception.Message%2A> hem de <xref:System.Exception.InnerException%2A> özelliklerini ayarlayan. Dördüncü Oluşturucu özel durumu seri hale getirmek için kullanılır. Yeni özel durum sınıfları seri hale getirilebilir olmalıdır. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#15)]  
  
 Yeni özellikler özel durumu çözmek için yararlı olduğunda yalnızca özel durum sınıfına eklenmelidir. Türetilmiş özel durum sınıfına yeni özellikler eklenirse, eklenen bilgileri döndürmek için `ToString()` geçersiz kılınmalıdır.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Exceptions](~/_csharplang/spec/exceptions.md) ve [throw deyimleri](~/_csharplang/spec/statements.md#the-throw-statement) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
- [Özel durum hiyerarşisi](../../../standard/exceptions/index.md)
- [Özel Durum İşleme](./exception-handling.md)
