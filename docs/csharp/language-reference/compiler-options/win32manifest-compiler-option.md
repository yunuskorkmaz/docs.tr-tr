---
title: -win32manifest (C# derleyici seçenekleri)
ms.date: 07/20/2015
f1_keywords:
- /win32manifest
helpviewer_keywords:
- /win32manifest compiler option [C#]
- win32manifest compiler option [C#]
- -win32manifest compiler option [C#]
ms.assetid: 9460ea1b-6c9f-44b8-8f73-301b30a01de1
ms.openlocfilehash: 5fc8a89faaa7fac3413000afdf94b6a96b23ab6d
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606266"
---
# <a name="-win32manifest-c-compiler-options"></a>-win32manifest (C# derleyici seçenekleri)
Bir projenin Taşınabilir çalıştırılabilir (PE) dosyasına gömülecek Kullanıcı tanımlı bir Win32 uygulama bildirim dosyası belirtmek için **-win32manifest** seçeneğini kullanın.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32manifest: filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Özel bildirim dosyasının adı ve konumu.  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak, görsel C# derleyici Istenen "asInvoker" yürütme düzeyini belirten bir uygulama bildirimi katıştırır. Bu, bildirimi, yürütülebilir dosyanın oluşturulduğu klasörde, genellikle Visual Studio kullandığınızda bin\Debug veya bin\Release klasöründe oluşturur. Örneğin, istenen "highestAvailable" veya "requireAdministrator" yürütme düzeyini belirtmek için özel bir bildirim sağlamak istiyorsanız, dosyanın adını belirtmek için bu seçeneği kullanın.  
  
> [!NOTE]
>  Bu seçenek ve [-win32res (C# derleyici seçenekleri)](./win32res-compiler-option.md) seçeneği birbirini dışlıyor. Her iki seçeneği de aynı komut satırında kullanmayı denerseniz, bir derleme hatası alırsınız.  
  
 İstenen bir yürütme düzeyini belirten uygulama bildirimi olmayan bir uygulama, Windows 'daki Kullanıcı hesabı denetimi özelliği altında dosya/kayıt defteri sanallaştırmaya tabidir. Daha fazla bilgi için bkz. [Kullanıcı hesabı denetimi](/windows/access-protection/user-account-control/user-account-control-overview).  
  
 Uygulamanız, bu koşullardan biri doğru olduğunda sanallaştırmaya tabi olacaktır:  
  
- **-Nowin32manifest** seçeneğini kullanın ve **-win32res** seçeneğini kullanarak sonraki bir derleme adımında veya Windows kaynak (. res) dosyasının bir parçası olarak bir bildirim sağlamaz.  
  
- İstenen yürütme düzeyini belirtmeyen özel bir bildirim sağlarsınız.  
  
 Visual Studio varsayılan bir. manifest dosyası oluşturur ve yürütülebilir dosyanın yanı sıra hata ayıklama ve sürüm dizinlerinde depolar. Herhangi bir metin düzenleyicisinde bir tane oluşturarak ve sonra dosyayı projeye ekleyerek özel bir bildirim ekleyebilirsiniz. Alternatif olarak, **Çözüm Gezgini**' de **Proje** simgesine sağ tıklayıp **Yeni öğe Ekle**' ye ve ardından **uygulama bildirim dosyası**' na tıklayabilirsiniz. Yeni veya mevcut bildirim dosyanızı ekledikten sonra, **bildirim** açılan listesinde görünür. Daha fazla bilgi için bkz. [uygulama sayfası, proje TasarımcısıC#()](/visualstudio/ide/reference/application-page-project-designer-csharp).  
  
 Uygulama bildirimini özel derleme sonrası bir adım olarak veya bir Win32 kaynak dosyasının parçası olarak [-nowin32manifest (C# derleyici seçenekleri)](./nowin32manifest-compiler-option.md) seçeneğini kullanarak sağlayabilirsiniz. Uygulamanızın Windows Vista 'da dosya veya kayıt defteri sanallaştırmaya tabi olmasını istiyorsanız bu seçeneği kullanın. Bu, derleyicinin Taşınabilir çalıştırılabilir (PE) dosyasında varsayılan bir bildirim oluşturmasını ve katıştırmasını engeller.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Visual C# DERLEYICISININ bir PE 'ye eklediği varsayılan bildirimi gösterir.  
  
> [!NOTE]
>  Derleyici, XML 'e "MyApplication. app" standart bir uygulama adı ekler. Bu, uygulamaların Windows Server 2003 Service Pack 3 üzerinde çalışmasını sağlamak için geçici bir çözümdür.  
  
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

- [C# Derleyici Seçenekleri](./index.md)
- [-nowin32manifest (C# derleyici seçenekleri)](./nowin32manifest-compiler-option.md)
- [Proje ve Çözüm Özelliklerini Yönetme](/visualstudio/ide/managing-project-and-solution-properties)
