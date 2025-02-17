---
description: :-Nowarn hakkında daha fazla bilgi edinin
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 4fb7d39aef48ff1443c342367f9e20bb37f9c5e0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434868"
---
# <a name="-nowarn"></a>-nowarn

Derleyicinin uyarı oluşturma yeteneğini engeller.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`numberList`|İsteğe bağlı. Derleyicinin bastırmaları gereken uyarı KIMLIĞI numaralarının virgülle ayrılmış listesi. Uyarı kimlikleri belirtilmemişse, tüm uyarılar bastırılır.|  
  
## <a name="remarks"></a>Açıklamalar  

 `-nowarn`Seçeneği derleyicinin uyarı üretmesine neden olur. Tek bir uyarıyı gizlemek için, `-nowarn` iki nokta üst üste izleyen seçeneğe uyarı kimliğini sağlayın. Birden çok uyarı numarasını virgülle ayırın.  
  
 Uyarı tanımlayıcısının yalnızca sayısal kısmını belirtmeniz gerekir. Örneğin, kullanılmayan yerel değişkenlerin uyarısı olan BC42024 'i gizlemek istiyorsanız, öğesini belirtin `-nowarn:42024` .  
  
 Uyarı KIMLIĞI numaraları hakkında daha fazla bilgi için bkz. [Visual Basic uyarıları yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Visual Studio tümleşik geliştirme ortamında-nowarn 'yi ayarlamak için|  
|---|  
|1. **Çözüm Gezgini** bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **Derle** sekmesine tıklayın.<br />3. tüm uyarıları devre dışı bırakmak için **tüm uyarıları devre dışı bırak** onay kutusunu seçin.<br />     - veya -<br />     Belirli bir uyarıyı devre dışı bırakmak için, uyarının yanındaki açılan listeden **hiçbiri** ' ne tıklayın.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod derlenir `T2.vb` ve herhangi bir uyarı görüntülemez.  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod derlenir `T2.vb` ve kullanılmayan yerel değişkenler için uyarıları görüntülemez (42024).  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
- [Visual Basic'teki Uyarıları Yapılandırma](/visualstudio/ide/configuring-warnings-in-visual-basic)
