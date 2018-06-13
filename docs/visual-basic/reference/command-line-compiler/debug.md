---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18d74b8f0a7b319e08780a8db9175c7be16d932e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654154"
---
# <a name="-debug-visual-basic"></a>-debug (Visual Basic)
Hata ayıklama bilgileri oluşturmak ve çıktı dosyasında yerleştirmek derleyici neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. Belirtme `+` veya `/debug` hata ayıklama bilgileri oluşturmak ve bir .pdb dosyasını yerleştirmek derleyici neden olur. Belirtme `-` değil belirtme aynı etkiye sahip `/debug`.|  
|`full` &#124; `pdbonly`|İsteğe bağlı. Derleyici tarafından üretilen hata ayıklama bilgi türünü belirtir. Belirtmezseniz, `/debug:pdbonly`, varsayılan `full`, çalışan programa bir hata ayıklayıcısı eklemeniz sağlar. `pdbonly` Bağımsız değişkene izin veriyor kaynak kodu hata ayıklama Hata Ayıklayıcısı'ndaki program başlatılır, ancak yalnızca çalışan program için hata ayıklayıcı iliştirildiğinde assembly dili kodunu görüntüler.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama yapıları oluşturmak için bu seçeneği kullanın. Belirtmezseniz, `/debug`, `/debug+`, veya `/debug:full`, programınızın çıktı dosyasında hata ayıklama mümkün olmayacaktır.  
  
 Varsayılan olarak, hata ayıklama bilgileri değil yayılan (`/debug-`). Hata ayıklama bilgilerini göster için belirtmeniz `/debug` veya `/debug+`.  
  
 Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz: [bir görüntü Debug kolaylaştırma](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
|Ayarlanacak - Visual Studio tümleşik geliştirme ortamında hata ayıklama|  
|---|  
|1.  Seçili bir proje ile **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**. <br />2.  Tıklatın **derleme** sekmesi.<br />3.  Tıklatın **Gelişmiş derleme seçenekleri**.<br />4.  Değer değiştirme **hata ayıklama bilgisi üret** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çıkış dosyasında hata ayıklama bilgilerini koyar `App.exe`.  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
