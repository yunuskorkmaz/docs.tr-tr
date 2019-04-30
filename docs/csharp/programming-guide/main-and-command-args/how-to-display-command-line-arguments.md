---
title: 'Nasıl yapılır: Komut satırı bağımsız değişkenlerini - görüntüleme C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: b7018afa1272f4ae092863de6b7f9ef783001244
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61710933"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüleme (C# Programlama Kılavuzu)
Komut satırında yürütülebilir bir dosya için sağlanan bağımsız değişkenler için isteğe bağlı bir parametre üzerinden erişilebilir `Main`. Bağımsız değişken bir dize dizisi biçiminde sağlanır. Dizinin her öğesinin tek bağımsız değişken içeriyor. Bağımsız değişkenler arasındaki boşluk kaldırılır. Örneğin, kurgusal bir yürütülebilir komut satırı bu çağrıları göz önünde bulundurun:  
  
|Komut satırında giriş|Ana geçirilen bir dize dizisi|  
|----------------------------|-------------------------------------|  
|**executable.exe a b c.**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**bir executable.exe iki**|"bir"<br /><br /> "iki"|  
|**executable.exe "bir iki" üç**|"one two"<br /><br /> "üç"|  
  
> [!NOTE]
>  Visual Studio'da bir uygulamayı çalıştırırken, komut satırı bağımsız değişkenlerini belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Örnek  
 Bu örnek, bir komut satırı uygulamaya geçirilen komut satırı bağımsız değişkenlerini görüntüler. İlk giriş yukarıdaki tabloda gösterilen çıktıya içindir.  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [csc.exe Kullanarak Komut Satırı Derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md)
- [Nasıl yapılır: Erişim foreach kullanarak komut satırı bağımsız değişkenleri](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)
- [Ana() Dönüş Değerleri](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
