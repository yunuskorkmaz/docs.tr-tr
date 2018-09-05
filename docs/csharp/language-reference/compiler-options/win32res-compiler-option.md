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
ms.openlocfilehash: 96b0b089843495d35a54db43018688dbb4ffba2b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507516"
---
# <a name="-win32res-c-compiler-options"></a>-win32res (C# Derleyici Seçenekleri)
**-Win32res** seçeneği, çıkış dosyasında bir Win32 kaynağı ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Çıkış dosyanızı eklemek istediğiniz kaynak dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir Win32 kaynak dosyası ile oluşturulan [kaynak derleyici](../../language-reference/compiler-options/resource-compiler-option.md). Kaynak Derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .res dosyası oluşturulur.  
  
 Bir Win32 kaynağı sürümü içerebilir veya yardımcı olan bit eşlem (simge) bilgilerini ve dosya Gezgini'ndeki uygulamanız belirleyin. Siz belirtmezseniz **-win32res**, derleyici derleme sürümünü temel alan sürüm bilgisi oluşturur.  
  
 Bkz: [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (için başvuru) veya [-kaynak](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açın **özellikleri** sayfası.  
  
2.  Tıklayın **uygulama** özellik sayfası.  
  
3.  Tıklayarak **kaynak dosyası** düğmesine tıklayın ve açılan kutuyu kullanarak bir dosyayı seçin.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve bir Win32 kaynak dosyası ekleme `rf.res` üretmek için `in.exe`:  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
