---
title: -ana (C# Derleyici Seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /main
helpviewer_keywords:
- -main compiler option [C#]
- main compiler option [C#]
- /main compiler option [C#]
ms.assetid: 975cf4d5-36ac-4530-826c-4aad0c7f2049
ms.openlocfilehash: 6c842abc1423e7ee0d98b71392e02410c6cf9172
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602728"
---
# <a name="-main-c-compiler-options"></a>-ana (C# Derleyici Seçenekleri)
Bu seçenek, birden fazla sınıf **bir Ana** yöntem içeriyorsa, programa giriş noktası içeren sınıfı belirtir.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-main:class  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
 `class`  
 **Ana** yöntemi içeren tür.  
 Verilen sınıf adı tam nitelikli olmalıdır; sınıfı içeren tam ad alanını içermelidir ve ardından sınıf adı olmalıdır. Örneğin, `Main` yöntem `Program` `MyApplication.Core` ad alanında sınıfın içinde bulunduğunda, derleyici seçeneği . `-main:MyApplication.Core.Program`
  
## <a name="remarks"></a>Açıklamalar  
 Derlemeniz [Ana](../../programming-guide/main-and-command-args/index.md) yönteme sahip birden fazla tür içeriyorsa, programa giriş noktası olarak kullanmak istediğiniz **Ana** yöntemi hangi türde içerdiğini belirtebilirsiniz.  
  
 Bu seçenek, bir .exe dosyası derlenirken kullanım içindir.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Bu derleyici seçeneğini Visual Studio geliştirme ortamında ayarlamak için  
  
1. Projenin **Özellikleri** sayfasını açın.  
  
2. **Uygulama** özelliği sayfasını tıklatın.  
  
3. Başlangıç **nesnesi** özelliğini değiştirin.  
  
     Bu derleyici seçeneğini programlı olarak <xref:VSLangProj80.ProjectProperties3.StartupObject%2A>ayarlamak için bkz.  
  
## <a name="example"></a>Örnek  
 Derleme `t2.cs` ve `t3.cs`, **Ana** yöntem in `Test2`bulunacağını belirten:  
  
```console  
csc t2.cs t3.cs -main:Test2  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# Derleyici Seçenekleri](./index.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
