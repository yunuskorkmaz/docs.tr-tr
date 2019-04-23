---
title: -nowarn (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 13bb50366d9c19751ef3387baf809ab69e27b5dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59324155"
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (C# Derleyici Seçenekleri)
**- Nowarn** seçeneği derleyici, bir veya daha fazla uyarı görüntülenmesini bastır olanak sağlar. Birden çok uyarı numaralarını virgülle ayırın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Arguments  
 `number1`, `number2`  
 Derleyicinin bastırmak için istediğiniz uyarı numaraları.  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca sayısal parçası uyarı tanımlayıcısının belirtmeniz gerekir. CS0028 gizlemek istiyorsanız, örneğin, belirtebilirsiniz `-nowarn:28`.  
  
 Derleyici uyarı numaralarını geçirilen sessizce yoksayar `-nowarn` , önceki sürümlerde geçerli, ancak derleyicisinden kaldırıldı. Örneğin, CS0679 geçerli Visual Studio .NET 2002 ancak daha sonra kaldırıldı.  
  
 Aşağıdaki uyarılar tarafından gizlenen olamaz `-nowarn` seçeneği:  
  
-   Derleyici Uyarısı (düzey 1) CS2002  
  
-   Derleyici Uyarısı (düzey 1) CS2023  
  
-   Derleyici Uyarısı (düzey 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Açık **özellikleri** proje sayfası. Ayrıntılar için bkz [derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Tıklayın **derleme** özellik sayfası.  
  
3. Değiştirme **uyarıları gösterme** özelliği.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [C# Derleyici Hataları](../../../csharp/language-reference/compiler-messages/index.md)
