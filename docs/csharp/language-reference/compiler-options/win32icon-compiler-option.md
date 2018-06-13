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
ms.openlocfilehash: ba5c7fcc8fe9e3eaab0a955f4cd1a1e07169049e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216209"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (C# Derleyici Seçenekleri)
**-Win32icon** seçeneği çıkış dosyasını ve dosya Gezgini'ndeki istenen çalışmasıdır çıktı dosyasında bir .ico dosyasını ekler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Çıkış dosyanızın eklemek istediğiniz .ico dosyasını.  
  
## <a name="remarks"></a>Açıklamalar  
 Bir .ico dosyasını ile oluşturulan [kaynak derleyici](https://msdn.microsoft.com/library/aa381042.aspx). Kaynak derleyicisi bir Visual C++ programını derleme yaparken çağrılır; .rc dosyasından bir .ico dosyası oluşturulur.  
  
 Bkz: [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) (için başvuru) veya [-kaynak](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası. Bkz: [-win32res](../../../csharp/language-reference/compiler-options/win32res-compiler-option.md) .res dosyasını içeri aktarmak için.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açmak **özellikleri** sayfaları.  
  
2.  Tıklatın **uygulama** özellik sayfası.  
  
3.  Değiştirme **uygulama simgesi** özelliği.  
  
 Bu derleyici seçeneği programlı olarak nasıl ayarlanacağı hakkında daha fazla bilgi için bkz: <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `in.cs` ve bir .ico dosyasını ekleyin `rf.ico` üretmek için `in.exe`:  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)  
 [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
