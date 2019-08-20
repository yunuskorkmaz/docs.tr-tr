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
ms.openlocfilehash: 605a28f8f804c11a9a6636c7a17ec5782cc5a429
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69590307"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Özel Durumlar Oluşturma ve Atma (C# Programlama Kılavuzu)
Özel durumlar, programı çalıştırırken bir hata oluştuğunu göstermek için kullanılır. Bir hatayı tanımlayan özel durum nesneleri oluşturulur ve [throw](../../language-reference/keywords/throw.md) anahtar sözcüğüyle oluşturulur. Çalışma zamanı, en uyumlu özel durum işleyicisini arar.  
  
 Aşağıdaki koşullardan biri veya daha fazlası doğru olduğunda programcılar özel durumlar atmalıdır:  
  
- Yöntem, tanımlı işlevini tamamlayamıyor.  
  
     Örneğin, bir yönteme ait bir parametre geçersiz bir değere sahipse:  
  
     [!code-csharp[csProgGuideExceptions#12](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#12)]  
  
- Nesne durumuna bağlı olarak bir nesneye uygun olmayan bir çağrı yapılır.  
  
     Bir örnek, salt okunurdur bir dosyaya yazmaya çalışıyor olabilir. Bir nesne durumunun bir işleme izin vermediği durumlarda, bu sınıfın bir türetmesi temelinde bir <xref:System.InvalidOperationException> örneği veya nesnesi oluşturun. Bu, bir <xref:System.InvalidOperationException> nesnesi oluşturan bir yönteme örnektir:  
  
     [!code-csharp[csProgGuideExceptions#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#13)]  
  
- Bir yöntemin bağımsız değişkeni bir özel duruma neden olur.  
  
     Bu durumda, özgün özel durum yakalanmalı ve bir <xref:System.ArgumentException> örnek oluşturulmalıdır. Özgün özel durum, <xref:System.ArgumentException> <xref:System.Exception.InnerException%2A> parametresi olarak öğesinin oluşturucusuna geçirilmelidir:  
  
     [!code-csharp[csProgGuideExceptions#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#14)]  
  
 Özel durumlar adlı <xref:System.Exception.StackTrace%2A>bir özelliği içerir. Bu dize, geçerli çağrı yığınındaki yöntemlerin adını, her yöntem için özel durumun oluşturulduğu dosya adı ve satır numarasıyla birlikte içerir. Bir <xref:System.Exception.StackTrace%2A> nesne, `throw` deyimin noktasındaki ortak dil çalışma zamanı (CLR) tarafından otomatik olarak oluşturulur. böylece, yığın izlemenin başlayacağı noktadan özel durumlar oluşturulmalıdır.  
  
 Tüm özel durumlar adlı <xref:System.Exception.Message%2A>bir özelliği içerir. Bu dize, özel durumun nedenini açıklamak için ayarlanmalıdır. Güvenliğe duyarlı bilgilerin ileti metnine yerleştirilmemelidir. Öğesinin buna ek <xref:System.Exception.Message%2A>olarak <xref:System.ArgumentException> , özel durumun oluşturulmasına <xref:System.ArgumentException.ParamName%2A> neden olan bağımsız değişkenin adı olarak ayarlanması gereken adlı bir özelliği içerir. Özellik ayarlayıcı söz konusu olduğunda, <xref:System.ArgumentException.ParamName%2A> olarak `value`ayarlanmalıdır.  
  
 Ortak ve korumalı Yöntemler, kendilerine amaçlanan işlevleri tamamlanamadığında özel durumlar atmalıdır. Oluşturulan özel durum sınıfı, hata koşullarına uyan en belirgin özel durum olmalıdır. Bu özel durumlar, sınıf işlevselliğinin bir parçası olarak belgelenmelidir ve özgün sınıftaki türetilmiş sınıflar veya güncelleştirmeler geriye dönük uyumluluk için aynı davranışı korurlar.  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a>Özel durumlar oluştururken kaçınmak için gerekenler  
 Aşağıdaki liste, özel durumlar oluştururken kaçınmak için Yöntemler tanımlar:  
  
- Özel durumlar, bir programın akışını sıradan yürütmenin parçası olarak değiştirmek için kullanılmamalıdır. Özel durumlar yalnızca hata koşullarını raporlamak ve işlemek için kullanılmalıdır.  
  
- Özel durumlar, oluşturulması yerine dönüş değeri veya parametresi olarak döndürülmemelidir.  
  
- Kendi kaynak kodunuzla <xref:System.SystemException?displayProperty=nameWithType> <xref:System.Exception?displayProperty=nameWithType> <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> ,, veya kasıtlı olarak kullanmayın<xref:System.NullReferenceException?displayProperty=nameWithType>.  
  
- Hata ayıklama modunda, ancak serbest bırakma modunda oluşturulabilecek özel durumlar oluşturmayın. Geliştirme aşamasında çalışma zamanı hatalarını belirlemek için bunun yerine hata ayıklama onayı kullanın.  
  
## <a name="defining-exception-classes"></a>Özel durum sınıfları tanımlama  
 Programlar, <xref:System> ad alanında önceden tanımlanmış bir özel durum sınıfı oluşturabilir (daha önce belirtilen durumlar hariç) veya ' den <xref:System.Exception>türeterek kendi özel durum sınıflarını oluşturabilir. Türetilmiş sınıflar en az dört Oluşturucu tanımlamalıdır: tek parametresiz bir Oluşturucu, ileti özelliğini ayarlayan diğeri ve hem hem de <xref:System.Exception.Message%2A> <xref:System.Exception.InnerException%2A> özelliklerini ayarlayan. Dördüncü Oluşturucu özel durumu seri hale getirmek için kullanılır. Yeni özel durum sınıfları seri hale getirilebilir olmalıdır. Örneğin:  
  
 [!code-csharp[csProgGuideExceptions#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#15)]  
  
 Yeni özellikler özel durumu çözmek için yararlı olduğunda yalnızca özel durum sınıfına eklenmelidir. Türetilmiş özel durum sınıfına yeni özellikler eklenirse, `ToString()` eklenen bilgileri döndürmek için geçersiz kılınmalıdır.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  

Daha fazla bilgi için bkz. [ C# dil belirtiminde](../../language-reference/language-specification/index.md) [Exceptions](~/_csharplang/spec/exceptions.md) ve [throw deyimleri](~/_csharplang/spec/statements.md#the-throw-statement) . Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Özel Durumlar ve Özel Durum İşleme](./index.md)
- [Özel durum hiyerarşisi](../../../standard/exceptions/index.md)
- [Özel Durum İşleme](./exception-handling.md)
