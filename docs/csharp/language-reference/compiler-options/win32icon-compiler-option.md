---
title: -win32icon (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: 5014b1da714f8e29f869d4641da93796a607aa4d
ms.sourcegitcommit: ba5c189bf44d44204a3e8838e59ec378a62d82f3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/12/2018
ms.locfileid: "44699271"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (C# Derleyici Seçenekleri)
**-Win32icon** seçeneği çıktı dosyasına dosya Gezgini'nde istenen görünümü verir çıkış dosyasına bir .ico simge dosyası ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Çıkış dosyanızı eklemek istediğiniz .ico dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir .ico simge dosyası ile oluşturulan [kaynak derleyici](/windows/desktop/menurc/resource-compiler). Kaynak derleyicisi, bir Visual C++ programını derlerken çağrılır; .rc dosyasından bir .ico simge dosyası oluşturulur.  
  
 Bkz: [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (için başvuru) veya [-kaynak](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası. Bkz: [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) bir .res dosyası içeri aktarmak için.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açın **özellikleri** sayfaları.  
  
2.  Tıklayın **uygulama** özellik sayfası.  
  
3.  Değiştirme **uygulama simgesi** özelliği.  
  
 Bu derleyici seçeneğini program üzerinden ayarlamak konusunda daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve bir .ico simge dosyası ekleme `rf.ico` üretmek için `in.exe`:  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
