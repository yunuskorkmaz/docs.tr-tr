---
title: "Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 557e72342901fab8bbe66e9cc3405cb4b2d9c1e2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>Nasıl yapılır: foreach Kullanarak Komut Satırı Bağımsız Değişkenlerine Erişme (C# Programlama Kılavuzu)
Dizi yineleme için başka bir yaklaşım kullanmaktır [foreach](../../../csharp/language-reference/keywords/foreach-in.md) Bu örnekte gösterildiği gibi deyimi. `foreach` deyimi, <xref:System.Collections.IEnumerable> ara birimini uygulayan bir dizi, .NET Framework koleksiyon sınıfı veya herhangi bir sınıf ya da yapının yinelenmesi için kullanılır.  
  
> [!NOTE]
>  Bir uygulamayı Visual Studio'da çalıştırırken, komut satırı bağımsız değişkenleri belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `foreach`kullanarak komut satırı değişkenlerinin nasıl yazdırılacağı gösterilir.  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Array>  
 <xref:System.Collections>  
 [Komut satırı csc.exe derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [foreach,](../../../csharp/language-reference/keywords/foreach-in.md)  
 [Ana() ve komut satırı bağımsız değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Nasıl yapılır: komut satırı bağımsız değişkenlerini görüntüleme](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)  
 [Ana() dönüş değerleri](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
