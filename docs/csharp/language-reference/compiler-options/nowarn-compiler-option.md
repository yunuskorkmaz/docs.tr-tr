---
description: -nowarn (C# derleyici seçenekleri)
title: -nowarn (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: 31a7ee5eacb2e7cd6b24c4a2276ce6e07fcc67e1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91194030"
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (C# derleyici seçenekleri)

**-Nowarn** seçeneği, derleyicinin bir veya daha fazla uyarı görüntülemesini engellemenize olanak tanır. Birden çok uyarı numarasını virgülle ayırın.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `number1`, `number2`  
 Derleyicinin görüntülenmesini istediğiniz uyarı numaraları.  
  
## <a name="remarks"></a>Açıklamalar  

 Uyarı tanımlayıcısının yalnızca sayısal bölümünü belirtmeniz gerekir. Örneğin, CS0028 bastırmak istiyorsanız, belirtebilirsiniz `-nowarn:28` .  
  
 Derleyici `-nowarn` önceki sürümlerde geçerli olan, ancak derleyicisinden kaldırılan uyarı numaralarını sessizce yok sayacaktır. Örneğin, CS0679 Visual Studio .NET 2002 derleyicisinde geçerliyse, ancak daha sonra kaldırılmıştır.  
  
 Aşağıdaki uyarılar seçenek tarafından gizlenemez `-nowarn` :  
  
- Derleyici Uyarısı (düzey 1) CS2002  
  
- Derleyici Uyarısı (düzey 1) CS2023  
  
- Derleyici Uyarısı (düzey 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın. Ayrıntılar için bkz. [derleme sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Uyarıları bastır** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A> ..  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [C# derleyici hataları](../compiler-messages/index.md)
