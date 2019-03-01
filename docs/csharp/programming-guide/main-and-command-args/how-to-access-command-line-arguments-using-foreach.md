---
title: 'Nasıl yapılır: Foreach kullanarak komut satırı bağımsız değişkenlerine erişim - C# Programlama Kılavuzu'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#]
ms.assetid: 89c3e335-3f5b-4e24-8c5a-b8036561fe8a
ms.openlocfilehash: 5813ad573e89886ba991ca8cbcebb7232af05821
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56971682"
---
# <a name="how-to-access-command-line-arguments-using-foreach-c-programming-guide"></a>Nasıl yapılır: Erişim foreach kullanarak komut satırı bağımsız değişkenleri (C# Programlama Kılavuzu)
Başka bir dizi yineleme yaklaşımı kullanmaktır [foreach](../../../csharp/language-reference/keywords/foreach-in.md) Bu örnekte gösterildiği gibi bir ifade. 
  `foreach` deyimi, <xref:System.Collections.IEnumerable> ara birimini uygulayan bir dizi, .NET Framework koleksiyon sınıfı veya herhangi bir sınıf ya da yapının yinelenmesi için kullanılır.  
  
> [!NOTE]
>  Visual Studio'da bir uygulama çalıştırırken, komut satırı bağımsız değişkenlerinde belirtebilirsiniz [hata ayıklama sayfası, Proje Tasarımcısı](/visualstudio/ide/reference/debug-page-project-designer).  
  
## <a name="example"></a>Örnek  
 Bu örnekte, `foreach`kullanarak komut satırı değişkenlerinin nasıl yazdırılacağı gösterilir.  
  
 [!code-csharp[csProgGuideMain#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class2.cs#10)]  
  
 [!code-csharp[csProgGuideMain#11](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#11)]  
  
## <a name="see-also"></a>Ayrıca bkz.

- <xref:System.Array>
- <xref:System.Collections>
- [csc.exe Kullanarak Komut Satırı Derleme](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)
- [C# Programlama Kılavuzu](../../../csharp/programming-guide/index.md)
- [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)
- [Ana() ve Komut Satırı Bağımsız Değişkenleri](../../../csharp/programming-guide/main-and-command-args/index.md)
- [Nasıl yapılır: Komut satırı bağımsız değişkenlerini görüntüleme](../../../csharp/programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [Ana() Dönüş Değerleri](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
