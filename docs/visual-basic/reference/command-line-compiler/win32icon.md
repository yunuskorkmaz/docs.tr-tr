---
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 6b4b69d227c857442de6857fac023090b3698e81
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004637"
---
# <a name="-win32icon"></a>-win32icon
Çıkış dosyasına bir. ico dosyası ekler. Bu. ico dosyası, **Dosya Gezgini**'nde çıkış dosyasını temsil eder.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
  
|Sözleşme Dönemi|Tanım|  
|---|---|  
|`filename`|Çıkış dosyanıza eklenecek. ico dosyası. Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  
 Microsoft Windows Kaynak derleyicisi (RC) ile bir. ico dosyası oluşturabilirsiniz. Visual C++ programı derlerken kaynak derleyicisi çağrılır; . ico dosyası. rc dosyasından oluşturulur. `-win32icon` Ve `-win32resource` seçenekleri birbirini dışlıyor.  
  
 Bir .NET Framework kaynak dosyasına başvurmak için bkz. [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) veya .NET Framework kaynak dosyası iliştirmek için [-Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) . . Res dosyasını içeri aktarmak için bkz. [-Win32Resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) .  
  
|Visual Studio IDE 'de set-win32icon|  
|---|  
|1. **Çözüm Gezgini**bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **uygulama** sekmesine tıklayın.<br />3. **simge** kutusunda değeri değiştirin.|  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod bir. `In.vb` ico dosyasını derler ve iliştirir `Rf.ico`.  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
