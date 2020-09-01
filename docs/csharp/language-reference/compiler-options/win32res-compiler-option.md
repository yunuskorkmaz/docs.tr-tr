---
description: -win32res (C# derleyici seçenekleri)
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
ms.openlocfilehash: c220c78a6d2c3109402a20f0de40fe9665d6c730
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140821"
---
# <a name="-win32res-c-compiler-options"></a>-win32res (C# derleyici seçenekleri)
**-Win32res** seçeneği çıkış dosyasına bir Win32 kaynağı ekler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  
 `filename`  
 Çıkış dosyanıza eklemek istediğiniz kaynak dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 [Kaynak derleyicisi](resource-compiler-option.md)Ile bir Win32 kaynak dosyası oluşturulabilir. Kaynak Derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .res dosyası oluşturulur.  
  
 Bir Win32 kaynağı, uygulamanızı dosya Gezgini 'nde tanımlamanızı sağlayacak sürüm veya bit eşlem (simge) bilgilerini içerebilir. **-Win32res**belirtmezseniz, derleyici derleme sürümünü temel alan sürüm bilgilerini oluşturacaktır.  
  
 Bir .NET Framework kaynak dosyası için bkz. [-linkresource](./linkresource-compiler-option.md) (başvuruya) veya [-Resource](./resource-compiler-option.md) (iliştirilecek).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Uygulama** Özellik sayfasına tıklayın.  
  
3. **Kaynak dosyası** düğmesine tıklayın ve açılan kutuyu kullanarak bir dosya seçin.  
  
## <a name="example"></a>Örnek  
 `in.cs`Üretmek için bir Win32 kaynak dosyası derleyin ve ekleyin `rf.res` `in.exe` :  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
