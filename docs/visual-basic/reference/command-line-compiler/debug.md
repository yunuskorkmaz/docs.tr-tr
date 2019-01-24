---
title: /debug (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: e32ce702847375c85a805926c56fb965a057ff03
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54605508"
---
# <a name="-debug-visual-basic"></a>-debug (Visual Basic)
Hata ayıklama bilgileri üret ve çıkış dosyalarına Kaydet yerleştirme derleyici neden olur.  
  
## <a name="syntax"></a>Sözdizimi  
  
```  
-debug[+ | -]  
' -or-  
-debug:[full | pdbonly]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Terim|Tanım|  
|---|---|  
|`+` &#124; `-`|İsteğe bağlı. Belirtme `+` veya `/debug` derleyicinin hata ayıklama bilgileri üret ve bir .pdb dosyası içinde yerleştirin. Belirtme `-` değil belirtmekle aynı etkiye sahip `/debug`.|  
|`full` &#124; `pdbonly`|İsteğe bağlı. Derleyici tarafından oluşturulan hata ayıklama bilgilerinin türünü belirtir. Siz belirtmezseniz `/debug:pdbonly`, varsayılan `full`, çalışan programa bir hata ayıklayıcının sağlar. `pdbonly` Bağımsız değişkene izin veriyor hata ayıklayıcıda program başlatıldı, ancak yalnızca çalışan programa hata ayıklayıcıya iliştirildiğinde derleme dili kodunu görüntüler. kaynak kodu hata ayıklama.|  
  
## <a name="remarks"></a>Açıklamalar  
 Hata ayıklama yapıları oluşturmak için bu seçeneği kullanın. Siz belirtmezseniz `/debug`, `/debug+`, veya `/debug:full`, çıkış dosyasında programınızın hata ayıklama mümkün olmayacaktır.  
  
 Varsayılan olarak, hata ayıklama bilgileri değil yayıldığını (`/debug-`). Hata ayıklama bilgilerini göster için belirtin `/debug` veya `/debug+`.  
  
 Bir uygulamanın hata ayıklama performansını yapılandırma hakkında daha fazla bilgi için bkz: [bir görüntü için hata ayıklama kolaylaştıracak](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
|Visual Studio tümleşik geliştirme ortamında ayarlamak için - hata ayıklama|  
|---|  
|1.  Seçili bir projeyle **Çözüm Gezgini**, **proje** menüsünde tıklatın **özellikleri**. <br />2.  Tıklayın **derleme** sekmesi.<br />3.  Tıklayın **Gelişmiş derleme seçenekleri**.<br />4.  Değer değiştirme **hata ayıklama bilgisi Oluştur** kutusu.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek çıkış dosyasında hata ayıklama bilgilerini koyar `App.exe`.  
  
```  
vbc -debug -out:app.exe test.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.
- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [/bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
