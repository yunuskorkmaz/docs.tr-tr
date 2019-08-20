---
title: Örnek COM sınıfı- C# Programlama Kılavuzu
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: 461d5a2afb197596c1c52daeeca0583b7b5e9693
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69589147"
---
# <a name="example-com-class-c-programming-guide"></a>Örnek COM Sınıfı (C# Programlama Kılavuzu)
Aşağıda bir COM nesnesi olarak kullanıma sunabileceğiniz bir sınıf örneği verilmiştir. Bu kod bir. cs dosyasına yerleştirildikten ve projenize eklendikten sonra, **com birlikte çalışma özelliğini kaydet** özelliğini **doğru**olarak ayarlayın. Daha fazla bilgi için [nasıl yapılır: COM birlikte çalışması](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100))için bir bileşeni kaydedin.
  
 Visual C# Objects 'i com 'a göstermek için bir sınıf arabirimi, gerekliyse bir olay arabirimi ve sınıfın kendisi için bildirim gerekir. Sınıf üyelerinin COM 'a görünür olması için bu kuralları izlemesi gerekir:  
  
- Sınıf ortak olmalıdır.  
  
- Özellikler, Yöntemler ve olaylar ortak olmalıdır.  
  
- Özellikler ve Yöntemler sınıf arabiriminde bildirilmelidir.  
  
- Olaylar olay arabiriminde bildirilmelidir.  
  
 Bu arabirimlerde bildirilmemiş olan sınıftaki diğer genel Üyeler COM 'a görünmez, ancak diğer .NET Framework nesneleri tarafından görülecektir.  
  
 Özellikleri ve yöntemleri com 'a sunmak için, bunları sınıf arabiriminde bildirmeniz ve bir `DispId` özniteliğiyle işaretlemeniz ve bunları sınıfında uygulamanız gerekir. Üyelerin arabirimde bildirildiği sıra, COM vtable için kullanılan sıradır.  
  
 Sınıfınızdan olayları göstermek için bunları olaylar arabiriminde bildirmeniz ve bir `DispId` özniteliğiyle işaretlemeniz gerekir. Sınıf bu arabirimi uygulamamalıdır.  
  
 Sınıfı sınıfı arabirimini uygular; birden fazla arabirim uygulayabilir, ancak ilk uygulama varsayılan sınıf arabirimi olur. COM 'a sunulan yöntemleri ve özellikleri buraya uygulayın. Bunların ortak olarak işaretlenmesi ve sınıf arabirimindeki bildirimlerle eşleşmesi gerekir. Ayrıca, burada sınıf tarafından oluşturulan olayları bildirin. Bunların ortak olarak işaretlenmesi ve olaylar arabirimindeki bildirimlerle eşleşmesi gerekir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Birlikte çalışabilirlik](./index.md)
- [Derleme Sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
