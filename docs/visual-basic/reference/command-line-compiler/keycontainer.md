---
title: -keycontainer
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b433182a502761fb3840ed2003cc50e053fb072a
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/22/2018
---
# <a name="-keycontainer"></a>-keycontainer
Bir derleme tanımlayıcı bir ad vermek bir anahtar çifti için bir anahtar kapsayıcı adı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-keycontainer:container  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`container`|Gerekli. Anahtar içeren kapsayıcı dosyası. Dosya adını tırnak işaretleri içine alın ("") adı boşluk içeriyorsa.|  
  
## <a name="remarks"></a>Açıklamalar  
 Derleyici, bir ortak anahtar derleme bildirimine ekleyerek ve son derlemeyi özel anahtarıyla açarak paylaşılabilir bir bileşen oluşturur. Bir anahtar dosyası oluşturmak için şunu yazın `sn -k``file` komut satırında. `-i` Seçeneği anahtar çiftini bir kapsayıcıya yükler. Daha fazla bilgi için bkz: [Sn.exe (tanımlayıcı ad aracı)][Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 İle derleme yaparsanız `-target:module`, anahtar dosyasının adı modülde tutulur ve bir derleme derlediğinizde oluşturduğunuz derlemesini birleştirilmiş [- addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).  
  
 Bu seçenek özel bir öznitelik belirtebilirsiniz (<xref:System.Reflection.AssemblyKeyNameAttribute>) herhangi bir Microsoft Ara dili (MSIL) modülü için kaynak kodundaki.  
  
 Derleyici ile şifreleme bilgilerinizi geçirebilirsiniz [- keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md). Kullanım [- delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) kısmen imzalı bir derleme istiyorsanız.  
  
 Bkz: [bkz](../../../framework/app-domains/create-and-use-strong-named-assemblies.md) derleme imzalama hakkında daha fazla bilgi için.  
  
> [!NOTE]
>  `-keycontainer` Seçeneği Visual Studio geliştirme ortamında kullanılabilir değil; yalnızca komut satırından derlerken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod kaynak dosyasını derler `Input.vb` ve bir anahtar kapsayıcısı belirtir.  
  
```  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Derlemeler ve Genel Derleme Önbelleği](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-keyfile](../../../visual-basic/reference/command-line-compiler/keyfile.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
