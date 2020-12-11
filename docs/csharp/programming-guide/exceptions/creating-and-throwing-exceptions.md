---
title: Özel durumlar oluşturma ve atma-C# Programlama Kılavuzu
description: Özel durumlar oluşturma ve atma hakkında bilgi edinin. Özel durumlar, bir program çalıştırılırken bir hata oluştuğunu göstermek için kullanılır.
ms.date: 12/09/2020
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
ms.openlocfilehash: a6998c5b274736b290460808ad4c7cb22be7ebf6
ms.sourcegitcommit: 9b877e160c326577e8aa5ead22a937110d80fa44
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97110214"
---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a>Özel Durumlar Oluşturma ve Atma (C# Programlama Kılavuzu)

Özel durumlar, programı çalıştırırken bir hata oluştuğunu göstermek için kullanılır. Bir hatayı tanımlayan özel durum nesneleri oluşturulur ve [throw](../../language-reference/keywords/throw.md) anahtar *sözcüğüyle oluşturulur.* Çalışma zamanı, en uyumlu özel durum işleyicisini arar.

Aşağıdaki koşullardan biri veya daha fazlası doğru olduğunda programcılar özel durumlar atmalıdır:

- Yöntemi, tanımlı işlevini tamamlayamıyor. Örneğin, bir yönteme ait bir parametre geçersiz bir değere sahipse:
  :::code language="csharp" source="snippets/exceptions/Program.cs" ID="CantComplete":::
- Nesne durumuna bağlı olarak bir nesneye uygun olmayan bir çağrı yapılır. Bir örnek, salt okunurdur bir dosyaya yazmaya çalışıyor olabilir. Bir nesne durumunun bir işleme izin vermediği durumlarda, <xref:System.InvalidOperationException> Bu sınıfın bir türetmesi temelinde bir örneği veya nesnesi oluşturun. Aşağıdaki kod, bir nesnesi oluşturan bir yönteme örnektir <xref:System.InvalidOperationException> :
  :::code language="csharp" source="snippets/exceptions/ProgramLog.cs" ID="ProgramLog":::
- Bir yöntemin bağımsız değişkeni bir özel duruma neden olur. Bu durumda, özgün özel durum yakalanmalı ve bir <xref:System.ArgumentException> örnek oluşturulmalıdır. Özgün özel durum, parametresi olarak öğesinin oluşturucusuna geçirilmelidir <xref:System.ArgumentException> <xref:System.Exception.InnerException%2A> :
  :::code language="csharp" source="snippets/exceptions/Program.cs" ID="InvalidArg":::

Özel durumlar adlı bir özelliği içerir <xref:System.Exception.StackTrace%2A> . Bu dize, geçerli çağrı yığınındaki yöntemlerin adını, her yöntem için özel durumun oluşturulduğu dosya adı ve satır numarasıyla birlikte içerir. Bir <xref:System.Exception.StackTrace%2A> nesne, deyimin noktasındaki ortak dil çalışma zamanı (CLR) tarafından otomatik olarak oluşturulur `throw` . böylece, yığın izlemenin başlayacağı noktadan özel durumlar oluşturulmalıdır.

Tüm özel durumlar adlı bir özelliği içerir <xref:System.Exception.Message%2A> . Bu dize, özel durumun nedenini açıklamak için ayarlanmalıdır. Güvenlik ile gizli olan bilgiler ileti metnine yerleştirmemelidir. Öğesinin buna ek olarak <xref:System.Exception.Message%2A> , <xref:System.ArgumentException> <xref:System.ArgumentException.ParamName%2A> özel durumun oluşturulmasına neden olan bağımsız değişkenin adı olarak ayarlanması gereken adlı bir özelliği içerir. Özellik ayarlayıcısı 'nda, <xref:System.ArgumentException.ParamName%2A> olarak ayarlanmalıdır `value` .

Ortak ve korumalı Yöntemler, kendilerine amaçlanan işlevleri tamamlanamadığında özel durumlar oluşturur. Oluşturulan özel durum sınıfı, hata koşullarına uyan en özel özel durumdur. Bu özel durumlar, sınıf işlevselliğinin bir parçası olarak belgelenmelidir ve özgün sınıftaki türetilmiş sınıflar veya güncelleştirmeler geriye dönük uyumluluk için aynı davranışı korurlar.

## <a name="things-to-avoid-when-throwing-exceptions"></a>Özel durumlar oluştururken kaçınmak için gerekenler

Aşağıdaki liste, özel durumlar oluştururken kaçınmak için Yöntemler tanımlar:

- Bir programın akışını sıradan yürütmenin parçası olarak değiştirmek için özel durumlar kullanmayın. Hata koşullarını bildirmek ve işlemek için özel durumları kullanın.
- Özel durumlar, bir dönüş değeri veya parametresi oluşturulması yerine döndürülmemelidir.
- <xref:System.Exception?displayProperty=nameWithType> <xref:System.SystemException?displayProperty=nameWithType> <xref:System.NullReferenceException?displayProperty=nameWithType> <xref:System.IndexOutOfRangeException?displayProperty=nameWithType> Kendi kaynak kodunuzla,, veya kasıtlı olarak oluşturmayın.
- Hata ayıklama modunda oluşturulabilecek, ancak serbest bırakma modunda oluşturulabilecek özel durumlar oluşturmayın. Geliştirme aşamasında çalışma zamanı hatalarını belirlemek için bunun yerine hata ayıklama onayı kullanın.

## <a name="defining-exception-classes"></a>Özel durum sınıfları tanımlama

Programlar, ad alanında önceden tanımlanmış bir özel durum sınıfı oluşturabilir <xref:System> (daha önce belirtilen durumlar hariç) veya ' den türeterek kendi özel durum sınıflarını oluşturabilir <xref:System.Exception> . Türetilmiş sınıflar en az dört Oluşturucu tanımlamalıdır: tek parametresiz bir Oluşturucu, ileti özelliğini ayarlayan diğeri ve hem hem de <xref:System.Exception.Message%2A> <xref:System.Exception.InnerException%2A> özelliklerini ayarlayan. Dördüncü Oluşturucu özel durumu seri hale getirmek için kullanılır. Yeni özel durum sınıfları seri hale getirilebilir olmalıdır. Örneğin:

:::code language="csharp" source="snippets/exceptions/InvalidDepartmentException.cs" id="DefineExceptionClass":::

Sağladığı veriler özel durumu çözmek için yararlı olduğunda, özel durum sınıfına yeni özellikler ekleyin. Türetilmiş özel durum sınıfına yeni özellikler eklenirse, `ToString()` eklenen bilgileri döndürmek için geçersiz kılınmalıdır.

## <a name="c-language-specification"></a>C# Dil Belirtimi

Daha fazla bilgi için [C# dil belirtiminde](/dotnet/csharp/language-reference/language-specification/introduction) [Exceptions](~/_csharplang/spec/exceptions.md) ve [throw deyimine](~/_csharplang/spec/statements.md#the-throw-statement) bakın. Dil belirtimi, C# sözdizimi ve kullanımı için kesin bir kaynaktır.

## <a name="see-also"></a>Ayrıca bkz.

- [Özel durum hiyerarşisi](../../../standard/exceptions/index.md)
