---
title: /debug (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f1c90b28f1df18e7e0a4f9e22730e1c3476fa650
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="debug-visual-basic"></a>/debug (Visual Basic)
Hata ayıklama bilgileri oluşturmak ve çıktı dosyasında yerleştirmek derleyici neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
/debug[+ | -]  
' -or-  
/debug:[full | pdbonly]  
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
  
|Tümleşik geliştirme ortamı/Debug Visual Studio'da ayarlamak için|  
|---|  
|1.  Seçili bir proje ile **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**. Daha fazla bilgi için bkz: [Proje Tasarımcısı giriş](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Tıklatın **derleme** sekmesi.<br />3.  Tıklatın **Gelişmiş derleme seçenekleri**.<br />4.  Değer değiştirme **hata ayıklama bilgisi üret** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çıkış dosyasında hata ayıklama bilgilerini koyar `App.exe`.  
  
```  
vbc /debug /out:app.exe test.vb  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)  
 [/ bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)  
 [Örnek derleme komut satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
