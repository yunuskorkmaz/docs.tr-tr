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
ms.openlocfilehash: 3f7f5f323006024c393cb066284712ed60836372
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="-win32res-c-compiler-options"></a>-win32res (C# Derleyici Seçenekleri)
**-Win32res** seçeneği bir Win32 kaynağı çıktı dosyasına ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Çıkış dosyanızın eklemek istediğiniz kaynak dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 Win32 kaynak dosyasını ile oluşturulan [kaynak derleyici](../../language-reference/compiler-options/resource-compiler-option.md). Kaynak Derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .res dosyası oluşturulur.  
  
 Win32 kaynak sürüm içerebilir veya yardımcı olacak bit eşlem (simgesi) bilgilerini dosya Gezgini uygulamanızda belirleyin. Belirtmezseniz, **-win32res**, derleyici derleme sürümünü temel alan sürüm bilgisini oluşturur.  
  
 Bkz: [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (için başvuru) veya [-kaynak](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **uygulama** özellik sayfası.  
  
3.  Tıklayın **kaynak dosyası** düğmesine tıklayın ve açılan kutuyu kullanarak bir dosya seçin.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve Win32 kaynak dosyası ekleme `rf.res` üretmek için `in.exe`:  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
