---
title: "-pdb (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /pdb
helpviewer_keywords:
- -pdb compiler option [C#]
- pdb compiler option [C#]
- /pdb compiler option [C#]
ms.assetid: e9d0f96a-5b75-45d6-9765-92538dd5f823
caps.latest.revision: "8"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 108244d7de49c2ff4df1ac7202e77958743b32df
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="pdb-c-compiler-options"></a>/pdb (C# Derleyici Seçenekleri)
**/Pdb** derleyici seçeneği, hata ayıklama simgeleri dosyasının konumunu ve adını belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/pdb:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Hata ayıklama simgeleri dosyasının konumunu ve adını.  
  
## <a name="remarks"></a>Açıklamalar  
 Belirttiğinizde [/Debug (C# Derleyici Seçenekleri)](../../../csharp/language-reference/compiler-options/debug-compiler-option.md), derleyici çıkış dosyasının adı ile aynı olan bir dosya adıyla derleyici çıktı dosyası (.exe veya .dll) oluşturur, bir .pdb dosyası ile aynı dizinde oluşturulur.  
  
 **/ pdb** varsayılan olmayan dosya adı ve .pdb dosyası için konum belirtmenize olanak tanır.  
  
 Visual Studio geliştirme ortamında bu derleyici seçeneği ayarlanamaz ya da programlı olarak değiştirilebilir.  
  
## <a name="example"></a>Örnek  
 Derleme `t.cs` ve tt.pdb adlı bir .pdb dosyası oluşturun:  
  
```console  
csc /debug /pdb:tt t.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)
