---
title: '-target: appcontainerexe (C# derleyici seçenekleri)'
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 09ae01d95138b72a0012f294189d288fc71c74b2
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606539"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target: appcontainerexe (C# derleyici seçenekleri)
**-Target: appcontainerexe** derleyici seçeneğini kullanırsanız, derleyici bir uygulama kapsayıcısında çalıştırılması gereken bir Windows çalıştırılabilir (. exe) dosyası oluşturur. Bu seçenek [-target: winexe](./target-winexe-compiler-option.md) ile eşdeğerdir, ancak uygulamalar için [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] tasarlanmıştır.  
  
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
  
     Bu seçenek yalnızca uygulama şablonları için [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] kullanılabilir.  
  
 Bu derleyici seçeneğini program aracılığıyla ayarlama hakkında daha fazla bilgi için bkz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki komut, yalnızca `filename.cs` bir uygulama kapsayıcısında çalıştırılabilen bir Windows yürütülebilir dosyası için derlenir.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [-target (C# derleyici seçenekleri)](./target-compiler-option.md)
- [-target: winexe (C# derleyici seçenekleri)](./target-winexe-compiler-option.md)
- [C# Derleyici Seçenekleri](./index.md)
