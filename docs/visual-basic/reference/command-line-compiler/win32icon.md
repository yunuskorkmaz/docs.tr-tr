---
description: Hakkında daha fazla bilgi edinin:-win32icon
title: -win32icon
ms.date: 03/13/2018
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
ms.openlocfilehash: 32a46771012708a42beb5450d28daf2fbab3f1c0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/14/2021
ms.locfileid: "100433555"
---
# <a name="-win32icon"></a>-win32icon

Çıkış dosyasına bir. ico dosyası ekler. Bu. ico dosyası, **Dosya Gezgini**'nde çıkış dosyasını temsil eder.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
  
|Terim|Tanım|  
|---|---|  
|`filename`|Çıkış dosyanıza eklenecek. ico dosyası. Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.|  
  
## <a name="remarks"></a>Açıklamalar  

 Microsoft Windows Kaynak derleyicisi (RC) ile bir. ico dosyası oluşturabilirsiniz. Visual C++ programı derlerken kaynak derleyicisi çağrılır; . ico dosyası. rc dosyasından oluşturulur. `-win32icon`Ve `-win32resource` seçenekleri birbirini dışlıyor.  
  
 Bir .NET Framework kaynak dosyasına başvurmak için bkz. [-linkresource (Visual Basic)](linkresource.md) veya .NET Framework kaynak dosyası iliştirmek için [-Resource (Visual Basic)](resource.md) . . Res dosyasını içeri aktarmak için bkz. [-Win32Resource](win32resource.md) .  
  
|Visual Studio IDE 'de set-win32icon|  
|---|  
|1. **Çözüm Gezgini** bir proje seçili olmalıdır. **Proje** menüsünde **Özellikler**' e tıklayın. <br />2. **uygulama** sekmesine tıklayın.<br />3. **simge** kutusunda değeri değiştirin.|  
  
## <a name="example"></a>Örnek  

 Aşağıdaki kod `In.vb` bir. ico dosyasını derler ve iliştirir `Rf.ico` .  
  
```console
vbc -win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic Command-Line derleyicisi](index.md)
- [Örnek Derleme Komut Satırları](sample-compilation-command-lines.md)
