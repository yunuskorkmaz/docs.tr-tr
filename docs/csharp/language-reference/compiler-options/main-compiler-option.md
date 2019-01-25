---
title: -main (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 36e5f10a61711e3245fa4b69dc583f4bb78e55e0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558594"
---
# <a name="-main-c-compiler-options"></a>-main (C# Derleyici Seçenekleri)
Birden fazla sınıf içeriyorsa, bu seçenek, giriş içeren sınıf noktası program belirtir bir **ana** yöntemi.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Arguments  
 `class`  
 İçeren tür **ana** yöntemi.  
 Belirtilen sınıf adı, tam olarak nitelenmiş olmalıdır; Bu sınıf adından önce gelen sınıfını içeren tam ad alanı içermelidir. Örneğin, `Main` yöntemi içinde bulunan `Program` sınıfını `MyApplication.Core` ad alanı, derleyici seçeneği sahip olacak şekilde `-main:MyApplication.Core.Program`.
  
## <a name="remarks"></a>Açıklamalar  
 Derlemeniz ile birden fazla tür içeriyorsa bir [ana](../../../csharp/programming-guide/main-and-command-args/index.md) yöntemi, hangi tür içeren belirtebilirsiniz **ana** programa giriş noktası olarak kullanmak istediğiniz yöntemi.  
  
 Bu seçenek, bir .exe dosyası derlenirken kullanım içindir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1.  Projenin açın **özellikleri** sayfası.  
  
2.  Tıklayın **uygulama** özellik sayfası.  
  
3.  Değiştirme **Başlangıç nesnesi** özelliği.  
  
     Bu derleyici seçeneğini program üzerinden ayarlamak için bkz: <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>.  
  
## <a name="example"></a>Örnek  
 Derleme `t2.cs` ve `t3.cs`, belirtilmesi, **ana** yöntemi bulunan `Test2`:  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](../../../csharp/language-reference/compiler-options/index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
