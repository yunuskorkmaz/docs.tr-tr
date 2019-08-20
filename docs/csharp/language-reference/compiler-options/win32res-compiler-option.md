---
title: -win32res (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 39f02c4c2e060c4be40002a2f48b0da31004a9ae
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606202"
---
# <a name="-win32res-c-compiler-options"></a>-win32res (C# derleyici seçenekleri)
**-Win32res** seçeneği çıkış dosyasına bir Win32 kaynağı ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Çıkış dosyanıza eklemek istediğiniz kaynak dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 [Kaynak derleyicisi](../../language-reference/compiler-options/resource-compiler-option.md)Ile bir Win32 kaynak dosyası oluşturulabilir. Kaynak Derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .res dosyası oluşturulur.  
  
 Bir Win32 kaynağı, uygulamanızı dosya Gezgini 'nde tanımlamanızı sağlayacak sürüm veya bit eşlem (simge) bilgilerini içerebilir. **-Win32res**belirtmezseniz, derleyici derleme sürümünü temel alan sürüm bilgilerini oluşturacaktır.  
  
 Bir .NET Framework kaynak dosyası için bkz. [-linkresource](./linkresource-compiler-option.md) (başvuruya) veya [-Resource](./resource-compiler-option.md) (iliştirilecek).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Uygulama** Özellik sayfasına tıklayın.  
  
3. **Kaynak dosyası** düğmesine tıklayın ve açılan kutuyu kullanarak bir dosya seçin.  
  
## <a name="example"></a>Örnek  
 `rf.res` Üretmek `in.cs` için`in.exe`bir Win32 kaynak dosyası derleyin ve ekleyin:  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
