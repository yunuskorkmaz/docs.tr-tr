---
description: -win32manifest (C# derleyici seçenekleri)
title: -win32manifest (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 1d2eefdab433f67e1cba5f709a2db8ec6b9a5dc7
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91171318"
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (C# derleyici seçenekleri)

Bir projenin Taşınabilir çalıştırılabilir (PE) dosyasına gömülecek Kullanıcı tanımlı bir Win32 uygulama bildirim dosyası belirtmek için **-win32manifest** seçeneğini kullanın.  
  
## <a name="syntax"></a>Söz dizimi  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Bağımsız değişkenler  

 `filename`  
 Özel bildirim dosyasının adı ve konumu.  
  
## <a name="remarks"></a>Açıklamalar  

 Varsayılan olarak, Visual C# derleyicisi, istenen "asInvoker" yürütme düzeyini belirten bir uygulama bildirimi katıştırır. Bu, bildirimi, yürütülebilir dosyanın oluşturulduğu klasörde, genellikle Visual Studio kullandığınızda bin\Debug veya bin\Release klasöründe oluşturur. Örneğin, istenen "highestAvailable" veya "requireAdministrator" yürütme düzeyini belirtmek için özel bir bildirim sağlamak istiyorsanız, dosyanın adını belirtmek için bu seçeneği kullanın.  
  
> [!NOTE]
> Bu seçenek ve [-win32res (C# derleyici seçenekleri)](./win32res-compiler-option.md) seçeneği birbirini dışlıyor. Her iki seçeneği de aynı komut satırında kullanmayı denerseniz, bir derleme hatası alırsınız.  
  
 İstenen bir yürütme düzeyini belirten uygulama bildirimi olmayan bir uygulama, Windows 'daki Kullanıcı hesabı denetimi özelliği altında dosya/kayıt defteri sanallaştırmaya tabidir. Daha fazla bilgi için bkz. [Kullanıcı hesabı denetimi](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Uygulamanız, bu koşullardan biri doğru olduğunda sanallaştırmaya tabi olacaktır:  
  
- **-Nowin32manifest** seçeneğini kullanın ve **-win32res** seçeneğini kullanarak sonraki bir derleme adımında veya Windows kaynak (. res) dosyasının bir parçası olarak bir bildirim sağlamaz.  
  
- İstenen yürütme düzeyini belirtmeyen özel bir bildirim sağlarsınız.  
  
 Visual Studio varsayılan bir. manifest dosyası oluşturur ve yürütülebilir dosyanın yanı sıra hata ayıklama ve sürüm dizinlerinde depolar. Herhangi bir metin düzenleyicisinde bir tane oluşturarak ve sonra dosyayı projeye ekleyerek özel bir bildirim ekleyebilirsiniz. Alternatif olarak, **Çözüm Gezgini**' de **Proje** simgesine sağ tıklayıp **Yeni öğe Ekle**' ye ve ardından **uygulama bildirim dosyası**' na tıklayabilirsiniz. Yeni veya mevcut bildirim dosyanızı ekledikten sonra, **bildirim** açılan listesinde görünür. Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (C#)](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Uygulama bildirimini, [-nowin32manifest (C# derleyici seçenekleri)](./nowin32manifest-compiler-option.md) seçeneğini kullanarak bir Win32 kaynak dosyasının parçası olarak veya bir Win32 kaynak dosyasının bir parçası olarak sağlayabilirsiniz. Uygulamanızın Windows Vista 'da dosya veya kayıt defteri sanallaştırmaya tabi olmasını istiyorsanız bu seçeneği kullanın. Bu, derleyicinin Taşınabilir çalıştırılabilir (PE) dosyasında varsayılan bir bildirim oluşturmasını ve katıştırmasını engeller.  
  
## <a name="example"></a>Örnek  

 Aşağıdaki örnek, Visual C# derleyicisinin bir PE 'ye eklediği varsayılan bildirimi gösterir.  
  
> [!NOTE]
> Derleyici, XML 'e "MyApplication. app" standart bir uygulama adı ekler. Bu, uygulamaların Windows Server 2003 Service Pack 3 üzerinde çalışmasını sağlamak için geçici bir çözümdür.  
  
```xml  
<?xml version="1.0" encoding="utf-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <assemblyIdentity version="1.0.0.0" name="MyApplication.app"/>  
  <trustInfo xmlns="urn:schemas-microsoft-com:asm.v2">  
    <security>  
      <requestedPrivileges xmlns="urn:schemas-microsoft-com:asm.v3">  
        <requestedExecutionLevel level="asInvoker"/>  
      </requestedPrivileges>  
    </security>  
  </trustInfo>  
</assembly>  
```  
  
## <a name="see-also"></a>Ayrıca bkz.

- [C# derleyici seçenekleri](./index.md)
- [-nowin32manifest (C# derleyici seçenekleri)](./nowin32manifest-compiler-option.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
