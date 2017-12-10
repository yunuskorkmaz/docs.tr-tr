---
title: "Birlikte Çalışabilirlik (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- COM interop
- interoperability
- platform invoke, accessing APIs with C#
- C# language, interoperability
ms.assetid: 238bb95a-e962-4026-bbd5-197055bdb8ee
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2965543066b0846a6a4f8a3199590049947122f2
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/09/2017
---
# <a name="interoperability-c-programming-guide"></a>Birlikte Çalışabilirlik (C# Programlama Kılavuzu)
Birlikte çalışabilirlik korumak ve yönetilmeyen kodunda Yatırımlar yararlanmak sağlar. Ortak dil çalışma zamanı (CLR) denetimi altında çalışan bir kod çağrılır *yönetilen kod*, ve CLR dışında çalışan kod çağrılır *yönetilmeyen kod*. COM, COM +, C++ bileşenleri, ActiveX bileşenlerini ve Microsoft Win32 API yönetilmeyen kod gösterilebilir.  
  
 [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] Platform yoluyla yönetilmeyen kod ile birlikte çalışabilirlik sağlar çağırma Hizmetleri <xref:System.Runtime.InteropServices> ad alanı, C++ birlikte çalışabilirlik ve COM birlikte çalışabilirliği (COM birlikte çalışma).  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Birlikte çalışabilirliğe genel bakış](../../../csharp/programming-guide/interop/interoperability-overview.md)  
 Yönetilmeyen kod ile C# yönetilen kodu arasında birlikte çalışmak için yöntemler açıklanmaktadır.  
  
 [Nasıl yapılır: Visual C# özelliklerini kullanarak Office birlikte çalışma nesnelerine erişim](../../../csharp/programming-guide/interop/how-to-access-office-onterop-objects.md)  
 Visual C Office programlama kolaylaştırmak için #'de kullanılmaya başlanmıştır özellikleri açıklar.  
  
 [Nasıl yapılır: Dizin oluşturulmuş özellikleri COM birlikte çalışma programlamada kullanma](../../../csharp/programming-guide/interop/how-to-use-indexed-properties-in-com-interop-rogramming.md)  
 Dizinli Özellikler parametrelere sahip erişim COM özellikleri için kullanmayı açıklar.  
  
 [Nasıl yapılır: Wave dosyasını oynatmak için Platform çağırma kullanma](../../../csharp/programming-guide/interop/how-to-use-platform-invoke-to-play-a-wave-file.md)  
 Platform kullanmayı açıklar Windows işletim sisteminde .wav ses dosyasını oynatmak için Hizmetleri çağırma.  
  
 [İzlenecek yol: Office programlama](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)  
 Bir Excel çalışma kitabı ve çalışma kitabı bağlantısını içeren bir Word belgesi nasıl oluşturulacağını gösterir.  
  
 [Örnek COM sınıfı](../../../csharp/programming-guide/interop/example-com-class.md)  
 Bir C# sınıf bir COM nesnesi olarak kullanıma sunmak gösterilmiştir.  
  
## <a name="c-language-specification"></a>C# Dil Belirtimi  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Yönetilmeyen kod ile birlikte çalışma](../../../../docs/framework/interop/index.md)  
 [İzlenecek yol: Office programlama](../../../csharp/programming-guide/interop/walkthrough-office-programming.md)
