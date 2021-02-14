---
description: Daha fazla bilgi edinin:-keycontainer
title: -keycontainer
ms.date: 03/10/2018
helpviewer_keywords:
- -keycontainer compiler option [Visual Basic]
- keycontainer compiler option [Visual Basic]
- /keycontainer compiler option [Visual Basic]
ms.assetid: 6a9bc861-1752-4db1-9f64-b5252f0482cc
ms.openlocfilehash: d8b83162d9404eb2ce80e5e531457360b040f27d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436818"
---
# <a name="-keycontainer"></a>-keycontainer

Bir derlemeye tanımlayıcı ad vermek için bir anahtar çifti için anahtar kapsayıcısı adı belirtir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-keycontainer:container  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`container`|Gereklidir. Anahtarı içeren kapsayıcı dosyası. Ad bir boşluk içeriyorsa, dosya adını tırnak işaretleri ("") içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  

 Derleyici, derleme bildirimine ortak anahtar ekleyerek ve son derlemeyi özel anahtarla imzalayarak paylaşılabilir bileşeni oluşturur. Anahtar dosyası oluşturmak için `sn -k file` komut satırına yazın. `-i`Seçeneği, anahtar çiftini bir kapsayıcıya kurar. Daha fazla bilgi için bkz. [Sn.exe (tanımlayıcı ad aracı)](../../../framework/tools/sn-exe-strong-name-tool.md)).  
  
 İle derlerseniz `-target:module` , anahtar dosyasının adı modülde tutulur ve [-addmodule](addmodule.md)ile bir derlemeyi derlerken oluşturulan derlemeye dahil edilir.  
  
 Bu seçeneği, <xref:System.Reflection.AssemblyKeyNameAttribute> herhangi bir Microsoft ara dili (MSIL) modülünün kaynak kodunda özel bir öznitelik () olarak da belirtebilirsiniz.  
  
 Ayrıca, [-keyfile](keyfile.md)ile şifreleme bilgilerinizi derleyiciye geçirebilirsiniz. Kısmen imzalanmış bir derleme istiyorsanız [-delaysign](delaysign.md) kullanın.  
  
 Bir derlemeyi imzalama hakkında daha fazla bilgi için bkz. [Strong-Named derlemeleri oluşturma ve kullanma](../../../standard/assembly/create-use-strong-named.md) .  
  
> [!NOTE]
> `-keycontainer`Bu seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod, kaynak dosyayı derler `Input.vb` ve bir anahtar kapsayıcısı belirtir.  
  
```console  
vbc -keycontainer:key1 input.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [.NET’te bütünleştirilmiş kodlar](../../../standard/assembly/index.md)
- [Visual Basic Command-Line derleyicisi](index.md)
- [-keyfile](keyfile.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
