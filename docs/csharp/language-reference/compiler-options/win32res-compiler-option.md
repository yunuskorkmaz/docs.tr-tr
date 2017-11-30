---
title: "-win32res (C# Derleyici Seçenekleri)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 96583542c62305cbaa5a24f66e9e54ec9b525c90
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2017
---
# <a name="win32res-c-compiler-options"></a>/win32res (C# Derleyici Seçenekleri)
**/Win32res** seçeneği bir Win32 kaynağı çıktı dosyasına ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
/win32res:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Çıkış dosyanızın eklemek istediğiniz kaynak dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 Win32 kaynak dosyasını ile oluşturulan [kaynak derleyici](../../language-reference/compiler-options/resource-compiler-option.md). Kaynak Derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .res dosyası oluşturulur.  
  
 Win32 kaynak sürüm içerebilir veya yardımcı olacak bit eşlem (simgesi) bilgilerini dosya Gezgini uygulamanızda belirleyin. Belirtmezseniz, **/win32res**, derleyici derleme sürümünü temel alan sürüm bilgisini oluşturur.  
  
 Bkz: [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (için başvuru) veya [/Resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfası.  
  
2.  Tıklatın **uygulama** özellik sayfası.  
  
3.  Tıklayın **kaynak dosyası** düğmesine tıklayın ve açılan kutuyu kullanarak bir dosya seçin.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve Win32 kaynak dosyası ekleme `rf.res` üretmek için `in.exe`:  
  
```console  
csc /win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve çözüm özelliklerini yönetme](/visualstudio/ide/managing-project-and-solution-properties)
