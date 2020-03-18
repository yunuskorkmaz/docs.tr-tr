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
ms.openlocfilehash: f3df92d8d0b0135eac1a055afafffa0015fecc2b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606280"
---
# <a name="-win32icon-c-compiler-options"></a>-win32icon (C# Derleyici Seçenekleri)
**-win32icon** seçeneği çıktı dosyasına bir .ico dosyası ekler ve bu da çıktı dosyasına Dosya Gezgini'nde istenen görünümü verir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32icon:filename  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `filename`  
 Çıktı dosyanıza eklemek istediğiniz .ico dosyası.  
  
## <a name="remarks"></a>Açıklamalar  
 [Kaynak Derleyicisi](/windows/desktop/menurc/resource-compiler)ile bir .ico dosyası oluşturulabilir. Visual C++ programı derlediğinizde Kaynak Derleyicisi çağrılır; .rc dosyasından bir .ico dosyası oluşturulur.  
  
 [Bkz.-linkresource](./linkresource-compiler-option.md) (başvuru için) veya [-kaynak](./resource-compiler-option.md) (eklemek için) bir .NET Framework kaynak dosyası. [Bkz.-win32res](./win32res-compiler-option.md) bir .res dosyasını almak için.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfalarını açın.  
  
2. **Uygulama** özelliği sayfasını tıklatın.  
  
3. Uygulama **simgesi** özelliğini değiştirin.  
  
 Bu derleyici seçeneğini programlı olarak nasıl ayarlayıştırılabildiğini öğrenmek için bkz. <xref:VSLangProj80.ProjectProperties3.ApplicationIcon%2A>  
  
## <a name="example"></a>Örnek  
 Derlemek `in.cs` ve üretmek `rf.ico` `in.exe`için bir .ico dosyası eklemek:  
  
```console  
csc -win32icon:rf.ico in.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
