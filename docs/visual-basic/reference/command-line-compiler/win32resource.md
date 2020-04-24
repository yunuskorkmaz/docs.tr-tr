---
title: -win32resource
ms.date: 03/13/2018
f1_keywords:
- -win32resource
- win32resource
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
ms.openlocfilehash: cee06adec89aac4b3e3f170df3bf932e466f3070
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004966"
---
# <a name="-win32resource"></a>-win32resource
Çıktı dosyasına bir Win32 kaynak dosyası ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32resource:filename  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `filename`  
 Çıkış dosyanıza eklenecek kaynak dosyasının adı. Bir boşluk içeriyorsa dosya adını tırnak işaretleri ("") içine alın.  
  
## <a name="remarks"></a>Açıklamalar  
 Microsoft Windows Kaynak derleyicisi (RC) ile bir Win32 kaynak dosyası oluşturabilirsiniz.  
  
 Win32 kaynağı, uygulamanızın **Dosya Gezgini**'nde tanımlanmasına yardımcı olan sürüm veya bit eşlem (simge) bilgilerini içerebilir. Belirtmezseniz `-win32resource`, derleyici derleme sürümüne göre sürüm bilgileri oluşturur. `-win32resource` Ve `-win32icon` seçenekleri birbirini dışlıyor.  
  
 Bir .NET Framework kaynak dosyasına başvurmak için bkz. [-linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) veya .NET Framework kaynak dosyası iliştirmek için [-Resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) .  
  
> [!NOTE]
> Bu `-win32resource` seçenek, Visual Studio geliştirme ortamı içinden kullanılamaz; yalnızca komut satırından derlenirken kullanılabilir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki kod, `Rf.res`bir `In.vb` Win32 kaynak dosyasını derler ve iliştirir:  
  
```console  
vbc -win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [Örnek Derleme Komut Satırları](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
