---
title: -win32manifest
ms.date: 03/13/2018
helpviewer_keywords:
- /win32manifest compiler option [Visual Basic]
- win32manifest compiler option [Visual Basic]
- -win32manifest compiler option [Visual Basic]
ms.assetid: 9e3191b4-90db-41c8-966a-28036fd20005
ms.openlocfilehash: cef1e6c19e7fdd6fc9f42c8fc36008314ea80a80
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349137"
---
# <a name="-win32manifest-visual-basic"></a>-win32manifest (Visual Basic)
Bir projenin taşınabilir yürütülebilir (PE) dosyasına gömülecek Kullanıcı tanımlı bir Win32 uygulama bildirim dosyası tanımlar.  
  
## <a name="syntax"></a>Sözdizimi  
  
```console  
-win32manifest: fileName  
```  
  
## <a name="arguments"></a>Bağımsız Değişkenler  
  
|Sözleşme Dönemi|Tanım|  
|---|---|  
|`fileName`|Özel bildirim dosyasının yolu.|  
  
## <a name="remarks"></a>Açıklamalar  
 Varsayılan olarak Visual Basic derleyici, istenen bir yürütme düzeyi olan asInvoker belirten bir uygulama bildirimi katıştırır. Bu, bildirim, yürütülebilir dosyanın oluşturulduğu klasörde, genellikle Visual Studio kullandığınızda bin\Debug veya bin\Release klasöründe oluşturulur. Özel bir bildirim sağlamak istiyorsanız, örneğin, bir highestAvailable veya requireAdministrator istenen yürütme düzeyini belirtmek için bu seçeneği, dosyanın adını belirtmek için kullanın.  
  
> [!NOTE]
> Bu seçenek ve [-Win32Resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) seçeneği birbirini dışlıyor. Her iki seçeneği de aynı komut satırında kullanmayı denerseniz, bir derleme hatası alırsınız.  
  
 İstenen bir yürütme düzeyini belirten uygulama bildirimi olmayan bir uygulama, Windows Vista 'daki Kullanıcı hesabı denetimi özelliği altında dosya/kayıt defteri sanallaştırmaya tabidir. Sanallaştırma hakkında daha fazla bilgi için bkz. [Windows Vista 'Da ClickOnce dağıtımı](/visualstudio/deployment/clickonce-deployment-on-windows-vista).  
  
 Aşağıdaki koşullardan biri doğru ise uygulamanız sanallaştırmaya tabi olacaktır:  
  
1. Seçeneğini kullanarak, `-nowin32manifest` seçeneğini kullanarak `-win32resource` sonraki bir derleme adımında veya bir Windows kaynak (. res) dosyasının parçası olarak bir bildirim sağlamaz.  
  
2. İstenen yürütme düzeyini belirtmeyen özel bir bildirim sağlarsınız.  
  
 Visual Studio varsayılan bir. manifest dosyası oluşturur ve yürütülebilir dosyanın yanı sıra hata ayıklama ve sürüm dizinlerinde depolar. Varsayılan App. manifest dosyasını, proje Tasarımcısı 'ndaki **uygulama** sekmesinde **UAC ayarlarını görüntüle** ' ye tıklayarak görüntüleyebilir veya düzenleyebilirsiniz. Daha fazla bilgi için bkz. [uygulama sayfası, proje Tasarımcısı (Visual Basic)](/visualstudio/ide/reference/application-page-project-designer-visual-basic).  
  
 Uygulama bildirimini özel derleme sonrası bir adım olarak veya `-nowin32manifest` seçeneğini kullanarak bir Win32 kaynak dosyasının parçası olarak sağlayabilirsiniz. Uygulamanızın Windows Vista 'da dosya veya kayıt defteri sanallaştırmaya tabi olmasını istiyorsanız bu seçeneği kullanın. Bu, derleyicinin PE dosyasında varsayılan bir bildirim oluşturmasını ve katıştırmasını engeller.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, Visual Basic derleyicisinin bir PE 'ye eklediği varsayılan bildirimi gösterir.  
  
> [!NOTE]
> Derleyici, bildirim XML dosyasına bir standart uygulama adı MyApplication. uygulaması ekler. Bu, uygulamaların Windows Server 2003 Service Pack 3 üzerinde çalışmasını sağlamak için geçici bir çözümdür.  
  
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

- [Visual Basic komut satırı derleyicisi](../../../visual-basic/reference/command-line-compiler/index.md)
- [-nowin32manifest (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nowin32manifest.md)
