---
title: '-target: appcontainerexe (C# derleyici seçenekleri)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 64661e72f9efe190606cadd93558678cb849e8cc
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204532"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target: appcontainerexe (C# derleyici seçenekleri)
**-Target: appcontainerexe** derleyici seçeneğini kullanırsanız, derleyici bir uygulama kapsayıcısında çalıştırılması gereken bir Windows çalıştırılabilir (. exe) dosyası oluşturur. Bu seçenek [-target: winexe](./target-winexe-compiler-option.md) ile eşdeğerdir, ancak Windows 8. x Mağazası uygulamaları için tasarlanmıştır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Uygulamanın bir uygulama kapsayıcısında çalışmasını gerektirmek için, bu seçenek [taşınabilir yürütülebilir](/windows/desktop/Debug/pe-format) (PE) dosyasında bir bit ayarlar. Bu bit ayarlandığında, CreateProcess yöntemi bir uygulama kapsayıcısının dışında yürütülebilir dosyayı başlatmaya çalışırsa bir hata oluşur.  
  
 [-Out](./out-compiler-option.md) seçeneğini kullanmadığınız takdirde, çıkış dosyası adı [Main](../../programming-guide/main-and-command-args/index.md) metodunu içeren giriş dosyasının adını alır.  
  
 Bu seçeneği bir komut isteminde belirttiğinizde, yürütülebilir dosyayı oluşturmak için bir sonraki **dışarı** veya **-hedef** seçeneğine kadar tüm dosyalar kullanılır.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Bu derleyici seçeneğini IDE içinde ayarlamak için  
  
1. **Çözüm Gezgini**' de, projeniz için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.  
  
2. **Uygulama** sekmesinde, **Çıkış türü** listesinde, **Windows Mağazası uygulaması**' nı seçin.  
  
     Bu seçenek yalnızca Windows 8. x Mağazası uygulama şablonları için kullanılabilir.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz. <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut `filename.cs`, yalnızca bir uygulama kapsayıcısında çalıştırılabilen bir Windows yürütülebilir dosyasına derler.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-target (C# derleyici seçenekleri)](./target-compiler-option.md)
- [-target: winexe (C# derleyici seçenekleri)](./target-winexe-compiler-option.md)
- [C# Derleyici Seçenekleri](./index.md)
