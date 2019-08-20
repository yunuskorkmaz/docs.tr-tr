---
title: -Main (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602728"
---
# <a name="-main-c-compiler-options"></a>-Main (C# derleyici seçenekleri)
Bu seçenek, birden fazla sınıf bir **Main** yöntemi içeriyorsa programa giriş noktasını içeren sınıfı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Arguments  
 `class`  
 **Main** metodunu içeren tür.  
 Belirtilen sınıf adı tam olarak nitelenmiş olmalıdır; sınıfını içeren tam ad alanını ve ardından sınıf adını içermelidir. Örneğin, `Main` yöntemi `MyApplication.Core` ad alanındaki `Program` sınıfının içindeyse, derleyici seçeneğinin olması gerekir `-main:MyApplication.Core.Program`.
  
## <a name="remarks"></a>Açıklamalar  
 Derlemeniz bir [ana](../../programming-guide/main-and-command-args/index.md) yöntemle birden fazla tür içeriyorsa, programa giriş noktası olarak kullanmak istediğiniz **ana** yöntemi içeren türü belirtebilirsiniz.  
  
 Bu seçenek bir. exe dosyası derlenirken kullanım içindir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikler** sayfasını açın.  
  
2. **Uygulama** Özellik sayfasına tıklayın.  
  
3. **Başlangıç nesnesi** özelliğini değiştirin.  
  
     Bu derleyici seçeneğini program aracılığıyla ayarlamak için, <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>bkz.  
  
## <a name="example"></a>Örnek  
 Ve `t2.cs` 'de`Test2`Main yönteminin bulunduğunu belirterek derleyin: `t3.cs`  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
