---
title: -win32icon (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32icon
helpviewer_keywords:
- win32icon compiler option [C#]
- /win32icon compiler option [C#]
- -win32icon compiler option [C#]
ms.assetid: 756d9b6d-ab07-41b7-ba58-5bd88f711138
ms.openlocfilehash: f3df92d8d0b0135eac1a055afafffa0015fecc2b
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606280"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (C# derleyici seçenekleri)
**-Win32icon** seçeneği çıkış dosyasına bir. ico dosyası ekler ve bu, çıktı dosyasına dosya Gezgini 'nde istenen görünümü verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Çıkış dosyanıza eklemek istediğiniz. ico dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 [Kaynak derleyicisi](/windows/desktop/menurc/resource-compiler)ile bir. ico dosyası oluşturulabilir. Visual C++ program derlerken kaynak derleyicisi çağrılır; . ico dosyası. rc dosyasından oluşturulur.  
  
 Bir .NET Framework kaynak dosyası için bkz. [-linkresource](./linkresource-compiler-option.md) (başvuruya) veya [-Resource](./resource-compiler-option.md) (iliştirilecek). . Res dosyasını içeri aktarmak için bkz. [-win32res](./win32res-compiler-option.md) .  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfalarını açın.  
  
2. **Uygulama** Özellik sayfasına tıklayın.  
  
3. **Uygulama simgesi** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>.  
  
## <a name="example"></a>Örnek  
 `rf.ico` Üretmek `in.cs` için`in.exe`bir. ico dosyası derleyin ve ekleyin:  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
