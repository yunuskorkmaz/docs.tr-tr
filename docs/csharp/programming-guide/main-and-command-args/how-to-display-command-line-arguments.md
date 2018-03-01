---
title: "Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme (C# Programlama Kılavuzu)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f6ae495eef227c6e4d9fb9ca0d4d0c031163fd52
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Nasıl yapılır: Komut Satırı Bağımsız Değişkenlerini Görüntüleme (C# Programlama Kılavuzu)
Komut satırında bir yürütülebilir dosya için sağlanan bağımsız değişkenler isteğe bağlı bir parametre üzerinden erişilebilir `Main`. Bağımsız değişken bir dize dizisi biçiminde sağlanır. Dizideki her öğe bir bağımsız değişken içeriyor. Boşluk bağımsız değişkenler arasındaki kaldırılır. Örneğin, bu komut satırı çağrılarını kurgusal bir yürütülebilir dosyanın göz önünde bulundurun:  
  
|Komut satırında giriş|Ana geçirilen bir dize dizisi|  
|----------------------------|-------------------------------------|  
|**executable.exe b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe bir iki**|"tek"<br /><br /> "iki"|  
|**executable.exe "bir iki" üç**|"one two"<br /><br /> "üç"|  
  
> [!NOTE]
>  Visual Studio'da Uygulama çalışırken, komut satırı bağımsız değişkenleri belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir komut satırı uygulamaya geçirilen komut satırı bağımsız değişkenleri görüntüler. İlk giriş yukarıdaki tabloda gösterilen çıkış içindir.  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# programlama kılavuzu](../../../csharp/programming-guide/index.md)  
 [Komut satırı csc.exe derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Ana() ve komut satırı bağımsız değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [Nasıl yapılır: foreach kullanarak komut satırı bağımsız değişkenlerine erişme](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Ana() dönüş değerleri](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
