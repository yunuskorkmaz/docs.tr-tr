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
ms.openlocfilehash: fa3079bf1431ba1a16b5a2eef0dd5500fe95909c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606618"
---
# <a name="-nowarn-c-compiler-options"></a>-nowarn (C# Derleyici Seçenekleri)
**-nowarn** seçeneği, derleyicinin bir veya daha fazla uyarı görüntülemesini bastırmanızı sağlar. Birden çok uyarı numaralarını virgülle ayırın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-nowarn:number1[,number2,...]  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `number1`, `number2`  
 Derleyicinin bastırmasını istediğiniz uyarı numarası(lar).  
  
## <a name="remarks"></a>Açıklamalar  
 Yalnızca uyarı tanımlayıcısının sayısal kısmını belirtmeniz gerekir. Örneğin, CS0028'i bastırmak istiyorsanız, bunu `-nowarn:28`belirtebilirsiniz.  
  
 Derleyici, önceki sürümlerde geçerli `-nowarn` olan, ancak derleyiciden kaldırılan uyarı numaralarını sessizce yok sayacaktır. Örneğin, CS0679 Visual Studio .NET 2002'deki derleyicide geçerliydi, ancak daha sonra kaldırıldı.  
  
 Aşağıdaki uyarılar `-nowarn` seçenek tarafından bastırılamaz:  
  
- Derleyici Uyarısı (düzey 1) CS2002  
  
- Derleyici Uyarısı (düzey 1) CS2023  
  
- Derleyici Uyarısı (düzey 1) CS2029  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın. Ayrıntılar için Bkz. [Build Page, Project Designer (C#)](/visualstudio/ide/reference/build-page-project-designer-csharp).  
  
2. Özellik **Oluştur** sayfasını tıklatın.  
  
3. Uyarıları **Bastır** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabilen ler hakkında bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.DelaySign%2A>  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
- [C# Derleyici Hataları](../compiler-messages/index.md)
