---
title: 'Nasıl yapılır: Foreach kullanarak komut satırı bağımsız değişkenlerine erişim - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 5dfddb0faf77e40397eafd70955e233a9a320163
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635825"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>Nasıl yapılır: Erişim foreach kullanarak komut satırı bağımsız değişkenleri (C# Programlama Kılavuzu)
Başka bir dizi yineleme yaklaşımı kullanmaktır [foreach](../../../csharp/language-reference/keywords/foreach-in.md) Bu örnekte gösterildiği gibi bir ifade. `foreach` deyimi, <xref:System.Collections.IEnumerable> ara birimini uygulayan bir dizi, .NET Framework koleksiyon sınıfı veya herhangi bir sınıf ya da yapının yinelenmesi için kullanılır.  
  
> [!NOTE]
>  Visual Studio'da bir uygulama çalıştırırken, komut satırı bağımsız değişkenlerinde belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `foreach`kullanarak komut satırı değişkenlerinin nasıl yazdırılacağı gösterilir.  
  
 [!code-csharp[csProgGuideMain#10](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_1.cs)]  
  
 [!code-csharp[csProgGuideMain#11](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-access-command-line-arguments-using-foreach_2.cs)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- <xref:System.Collections>
- [csc.exe Kullanarak Komut Satırı Derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md)
- [Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüleme](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Ana() Dönüş Değerleri](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
