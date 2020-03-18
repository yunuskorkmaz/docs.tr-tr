---
title: Örnek COM Sınıfı - C# Programlama Kılavuzu
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 6af85d0314a44acbde0996cecbe6dad82cdcc8db
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712084"
---
# <a name="example-com-class-c-programming-guide"></a>Örnek COM Sınıfı (C# Programlama Kılavuzu)
Aşağıda, COM nesnesi olarak ortaya çıkaracağınız bir sınıf örneği verilmiştir. Bu kod bir .cs dosyasına yerleştirildikten ve projenize eklendikten sonra COM **Interop özelliğini** **True**olarak ayarlayın. Daha fazla bilgi için [bkz: COM Interop için bir Bileşen kaydedin.](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100))
  
 Visual C# nesnelerinin COM'a teşhir edilmesi için bir sınıf arabirimi, gerekirse olaylar arabirimi ve sınıfın kendisini bildirme gerekir. Sınıf üyeleri COM tarafından görülebilmek için aşağıdaki kurallara uymalıdır:  
  
- Sınıf halka açık olmalı.  
  
- Özellikler, yöntemler ve olaylar herkese açık olmalıdır.  
  
- Özellikler ve yöntemler sınıf arabiriminde bildirilmelidir.  
  
- Olaylar olay arabiriminde bildirilmelidir.  
  
 Bu arabirimlerde bildirilmemiş sınıfdaki diğer ortak üyeler COM tarafından görülemez, ancak diğer .NET Framework nesneleri tarafından görünür olacaktır.  
  
 Özellikleri ve yöntemleri COM'a maruz bırakmak için, bunları sınıf `DispId` arabiriminde bildirmeniz ve bir öznitelikle işaretlemeniz ve bunları sınıfta uygulamanız gerekir. Üyelerin arabirimde beyan edildiği sıra, COM vtable için kullanılan sıradır.  
  
 Sınıfınızdaki olayları ortaya çıkarmak için, bunları olaylar arabiriminde `DispId` bildirmeniz ve bunları bir öznitelikle işaretlemeniz gerekir. Sınıf bu arabirimi uygulamamalıdır.  
  
 Sınıf arabirimini uygular; birden fazla arabirim uygulayabilir, ancak ilk uygulama varsayılan sınıf arabirimi olacaktır. COM'a maruz kalan yöntemleri ve özellikleri burada uygulayın. Bunlar genel olarak işaretlenmeli ve sınıf arabirimindeki bildirimlerle eşleşmelidir. Ayrıca, burada sınıf tarafından yetiştirilen olayları bildirin. Bunlar genel olarak işaretlenmeli ve olaylar arabirimindeki bildirimlerle eşleşmelidir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Birlikte çalışabilirlik](./index.md)
- [Derleme Sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
