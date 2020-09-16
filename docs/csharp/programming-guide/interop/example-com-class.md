---
title: Örnek COM sınıfı-C# Programlama Kılavuzu
description: C# ' de bir sınıfı COM nesnesi olarak kullanıma sunma hakkında bilgi edinin. Bu örnek, bir. cs dosyasındaki kodu bir projeye ekler ve COM birlikte çalışma özelliğini Kaydet özelliği ayarlar.
ms.date: 07/20/2015
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
ms.openlocfilehash: d49d391f5ea7717e0c36782be65cfb2ae154b843
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90542802"
---
# <a name="example-com-class-c-programming-guide"></a>Örnek COM Sınıfı (C# Programlama Kılavuzu)
Aşağıda bir COM nesnesi olarak kullanıma sunabileceğiniz bir sınıf örneği verilmiştir. Bu kod bir. cs dosyasına yerleştirildikten ve projenize eklendikten sonra, **com birlikte çalışma özelliğini kaydet** özelliğini **doğru**olarak ayarlayın. Daha fazla bilgi için bkz. [nasıl yapılır: bir BILEŞENI com birlikte çalışması Için kaydetme](/previous-versions/visualstudio/visual-studio-2010/w29wacsy(v=vs.100)).
  
 Visual C# nesnelerini COM 'a göstermek için bir sınıf arabirimi, gerekliyse bir olay arabirimi ve sınıfın kendisi için bildirim gerekir. Sınıf üyelerinin COM 'a görünür olması için bu kuralları izlemesi gerekir:  
  
- Sınıf ortak olmalıdır.  
  
- Özellikler, Yöntemler ve olaylar ortak olmalıdır.  
  
- Özellikler ve Yöntemler sınıf arabiriminde bildirilmelidir.  
  
- Olaylar olay arabiriminde bildirilmelidir.  
  
 Bu arabirimlerde bildirilmeyen sınıftaki diğer genel Üyeler COM 'a görünmez, ancak diğer .NET nesneleri tarafından görülecektir.  
  
 Özellikleri ve yöntemleri COM 'a sunmak için, bunları sınıf arabiriminde bildirmeniz ve bir `DispId` özniteliğiyle işaretlemeniz ve bunları sınıfında uygulamanız gerekir. Üyelerin arabirimde bildirildiği sıra, COM vtable için kullanılan sıradır.  
  
 Sınıfınızdan olayları göstermek için bunları olaylar arabiriminde bildirmeniz ve bir özniteliğiyle işaretlemeniz gerekir `DispId` . Sınıf bu arabirimi uygulamamalıdır.  
  
 Sınıfı sınıfı arabirimini uygular; birden fazla arabirim uygulayabilir, ancak ilk uygulama varsayılan sınıf arabirimi olur. COM 'a sunulan yöntemleri ve özellikleri buraya uygulayın. Bunların ortak olarak işaretlenmesi ve sınıf arabirimindeki bildirimlerle eşleşmesi gerekir. Ayrıca, burada sınıf tarafından oluşturulan olayları bildirin. Bunların ortak olarak işaretlenmesi ve olaylar arabirimindeki bildirimlerle eşleşmesi gerekir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInterop#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideInterop/CS/ExampleCOM.cs#8)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../index.md)
- [Birlikte çalışabilirlik](./index.md)
- [Derleme Sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
