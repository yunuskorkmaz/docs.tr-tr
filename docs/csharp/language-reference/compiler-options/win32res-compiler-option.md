---
title: -win32res (C# Derleyici Seçenekleri)
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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606202"
---
# <a name="-win32res-c-compiler-options"></a>-win32res (C# Derleyici Seçenekleri)
**-win32res** seçeneği, çıktı dosyasına bir Win32 kaynağı ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `filename`  
 Çıktı dosyanıza eklemek istediğiniz kaynak dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 [Kaynak Derleyicisi](../../language-reference/compiler-options/resource-compiler-option.md)ile Win32 kaynak dosyası oluşturulabilir. Kaynak Derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .res dosyası oluşturulur.  
  
 Win32 kaynağı, Dosya Gezgini'nde uygulamanızı tanımlamaya yardımcı olacak sürüm veya bitmap (simge) bilgileri içerebilir. **-win32res**belirtmezseniz, derleyici derleme sürümüne dayalı sürüm bilgileri oluşturur.  
  
 [Bkz.-linkresource](./linkresource-compiler-option.md) (başvuru için) veya [-kaynak](./resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. **Uygulama** özelliği sayfasını tıklatın.  
  
3. **Kaynak Dosyası** düğmesine tıklayın ve açılan kutuyu kullanarak bir dosya seçin.  
  
## <a name="example"></a>Örnek  
 Oluşturmak `in.cs` için win32 kaynak `rf.res` dosyasını `in.exe`derle ve ekle:  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
