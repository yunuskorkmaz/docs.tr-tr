---
title: -nowarn (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /nowarn
helpviewer_keywords:
- nowarn compiler option [C#]
- /nowarn compiler option [C#]
- -nowarn compiler option [C#]
ms.assetid: 6dcbc5e8-ae67-4566-9df3-f63cfdd9c4e4
ms.openlocfilehash: fa3079bf1431ba1a16b5a2eef0dd5500fe95909c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606618"
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (C# derleyici seçenekleri)
**-Nowarn** seçeneği, derleyicinin bir veya daha fazla uyarı görüntülemesini engellemenize olanak tanır. Birden çok uyarı numarasını virgülle ayırın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Arguments  
 `number1`, `number2`  
 Derleyicinin görüntülenmesini istediğiniz uyarı numaraları.  
  
## <a name="remarks"></a>Açıklamalar  
 Uyarı tanımlayıcısının yalnızca sayısal bölümünü belirtmeniz gerekir. Örneğin, CS0028 bastırmak istiyorsanız, belirtebilirsiniz `-nowarn:28`.  
  
 Derleyici önceki sürümlerde geçerli `-nowarn` olan, ancak derleyicisinden kaldırılan uyarı numaralarını sessizce yok sayacaktır. Örneğin, CS0679 Visual Studio .NET 2002 derleyicisinde geçerliyse, ancak daha sonra kaldırılmıştır.  
  
 Aşağıdaki uyarılar `-nowarn` seçenek tarafından gizlenemez:  
  
- Derleyici Uyarısı (düzey 1) CS2002  
  
- Derleyici Uyarısı (düzey 1) CS2023  
  
- Derleyici Uyarısı (düzey 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın. Ayrıntılar için bkz. [derleme sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. **Yapı** özelliği sayfasına tıklayın.  
  
3. **Uyarıları bastır** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [C# Derleyici Hataları](../compiler-messages/index.md)
