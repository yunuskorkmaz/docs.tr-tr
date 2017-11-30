---
title: "Örnek COM Sınıfı (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- examples [C#], COM classes
- COM, exposing Visual C# objects to
ms.assetid: 6504dea9-ad1c-4993-a794-830fec5270af
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ad14b414c037d38da55ce0ec82685b790cc46d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="example-com-class-c-programming-guide"></a>Örnek COM Sınıfı (C# Programlama Kılavuzu)
Bir COM nesnesi olarak kullanıma sunmak bir sınıfın bir örnek verilmiştir. Bu kod bir .cs dosyasında yerleştirilir ve projenize eklenen sonra kümesini **kaydetmek için COM birlikte çalışma** özelliğine **doğru**. Daha fazla bilgi için bkz: [NIB: nasıl yapılır: COM birlikte çalışma için bir bileşen Kaydol](http://msdn.microsoft.com/en-us/4de7d474-56e8-4027-994d-d47ca4725c5e).  
  
 Visual C# COM nesnelerini gösterme sınıf arabirimi, gerekli olduğunda olayları arabirim ve sınıf bildirme gerektirir. Sınıf üyeleri için COM görünür olması için bu kurallara uymalıdır:  
  
-   Sınıf ortak olmalıdır.  
  
-   Özellikleri, yöntemleri ve olayları ortak olmalıdır.  
  
-   Özellikleri ve yöntemleri sınıfı arabirimde bildirilmesi gerekir.  
  
-   Olaylar olay arabirimi bildirilmesi gerekir.  
  
 Bu arabirimleri bildirilmemiş diğer ortak sınıf üyelerine COM görünmez, ancak diğer .NET Framework nesneleri için görünür olacaktır.  
  
 Özellikleri ve yöntemleri com kullanıma sunmak için sınıf arabirimde bildirme ve bunlarla işaretlemek bir `DispId` özniteliği ve bunları sınıfında uygulama. Üyeleri bir arabirimde bildirilen sırası COM vtable için kullanılan sıradır.  
  
 Olaylar, sınıfından oluşturmak için olayları arabirimi bildirme ve bunlarla işaretlemek bir `DispId` özniteliği. Sınıfı bu arabirimi uygulamalıdır değil.  
  
 Sınıf sınıf arabirimi uygular; birden fazla arabirimi uygulayabilirsiniz, ancak ilk uygulaması varsayılan sınıf arabirimi olacaktır. Burada com'a özellikleri ve yöntemleri uygulayın. Bunlar ortak işaretlenmesi gerekir ve sınıf arabirimi bildirimlerinde eşleşmesi gerekir. Ayrıca, burada sınıfı tarafından tetiklenen olayları bildirin. Bunlar ortak işaretlenmesi gerekir ve olayları arabirimi bildirimlerinde eşleşmesi gerekir.  
  
## <a name="example"></a>Örnek  
 [!code-csharp[csProgGuideInterop#8](../../../csharp/programming-guide/interop/codesnippet/CSharp/example-com-class_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Birlikte çalışabilirlik](../../../csharp/programming-guide/interop/index.md)  
 [Derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp)
