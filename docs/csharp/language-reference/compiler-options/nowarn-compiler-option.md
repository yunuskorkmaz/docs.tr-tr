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
ms.openlocfilehash: 1c5e8bc7ad065c4662cd489930b2226e8a4b8962
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215491"
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (C# Derleyici Seçenekleri)
**- Nowarn** seçeneği bir veya daha fazla uyarı görüntülenmesini derleyici bastırmak olanak sağlar. Birden çok uyarı numaralarını virgülle ayırın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Arguments  
 `number1`, `number2`  
 Derleyicinin gizlemek için istediğiniz uyarı numaraları.  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca uyarı tanımlayıcı sayısal parçası belirtmeniz gerekir. Örneğin, CS0028 gizlemek istiyorsanız, belirttiğiniz `-nowarn:28`.  
  
 Derleyici öğesine iletilen uyarı numaralarını sessizce yoksayacak `-nowarn` , önceki sürümlerde geçerli ancak derleyiciden kaldırılmış. Örneğin, CS0679 Visual Studio .NET 2002 derleyicide geçerli ancak sonradan kaldırıldı.  
  
 Aşağıdaki uyarılarla tarafından gizlenen olamaz `-nowarn` seçeneği:  
  
-   Derleyici Uyarısı (düzey 1) CS2002  
  
-   Derleyici Uyarısı (düzey 1) CS2023  
  
-   Derleyici Uyarısı (düzey 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Açık **özellikleri** projesi için sayfa. Ayrıntılar için bkz [derleme sayfası, Proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2.  Tıklatın **yapı** özellik sayfası.  
  
3.  Değiştirme **uyarıları gösterme** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)  
 [C# Derleyici Hataları](../../../csharp/language-reference/compiler-messages/index.md)
