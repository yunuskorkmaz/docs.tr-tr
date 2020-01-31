---
title: "Nasıl yapılır: WPF Uygulamalarını Dağıtmak için IIS 5.0 ve IIS 6.0'ı Yapılandırma"
titleSuffix: ''
ms.date: 03/30/2017
helpviewer_keywords:
- MIME types [WPF], registering
- adjusting content expiration setting [WPF]
- registering file extensions [WPF]
- deploying applications [WPF]
- applications [WPF], deploying
- Web servers [WPF], configuring to deploy WPF applications
- configuring Web servers to deploy WPF applications [WPF]
- content expiration setting [WPF], adjusting
- file extensions [WPF], registering
- registering MIME types [WPF]
ms.assetid: c6e8c2cb-9ba2-4e75-a0d5-180ec9639433
ms.openlocfilehash: d557ac6cd380edcbc93b5315f6356697817274bf
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/24/2020
ms.locfileid: "76740412"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>Nasıl yapılır: WPF Uygulamalarını Dağıtmak için IIS 5.0 ve IIS 6.0'ı Yapılandırma

Uygun çok amaçlı Internet posta uzantıları (MIME) türleriyle yapılandırıldığı sürece, çoğu Web sunucusundan bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygulaması dağıtabilirsiniz. Varsayılan olarak, Microsoft Internet Information Services (IIS) 7,0 bu MIME türleriyle yapılandırılır, ancak Microsoft Internet Information Services (IIS) 5,0 ve Microsoft Internet Information Services (IIS) 6,0 değildir.

Bu konuda, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalarını dağıtmak için Microsoft Internet Information Services (IIS) 5,0 ve Microsoft Internet Information Services (IIS) 6,0 ' nin nasıl yapılandırılacağı açıklanmaktadır.

> [!NOTE]
> Bir sistemin .NET Framework yüklü olup olmadığını anlamak için kayıt defterindeki *UserAgent* dizesini kontrol edebilirsiniz. .NET Framework bir sistemde yüklü olup olmadığını belirlemek üzere *UserAgent* dizesini inceleyen Ayrıntılar ve bir betik için, bkz. [.NET Framework 3,0 'Nin yüklü olup olmadığını algılama](how-to-detect-whether-the-net-framework-3-0-is-installed.md).

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a>Içerik süre sonu ayarını ayarla

İçerik süre sonu ayarını 1 dakika olarak ayarlamanız gerekir. Aşağıdaki yordamda bunun IIS ile nasıl yapılacağı özetlenmektedir.

1. **Başlat** menüsüne tıklayın, **Yönetim Araçları**' nın üzerine gelın ve **Internet Information Services (IIS) Yöneticisi**' ne tıklayın. Bu uygulamayı komut satırından "%SystemRoot%\system32\inetsrv\iis.msc" ile de başlatabilirsiniz.

2. **Varsayılan Web sitesi** düğümünü bulana kadar IIS ağacını genişletin.

3. **Varsayılan Web sitesi** ' ne sağ tıklayın ve bağlam menüsünden **Özellikler** ' i seçin.

4. **Http üstbilgileri** sekmesini seçin ve "Içerik süre sonunu etkinleştir" e tıklayın.

5. İçeriği 1 dakika sonra dolacak şekilde ayarlayın.

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a>MIME türlerini ve dosya uzantılarını Kaydet

İstemci sistemindeki tarayıcının doğru işleyiciyi yükleyebilmesi için birkaç MIME türünü ve dosya uzantısını kaydetmeniz gerekir. Aşağıdaki türleri eklemeniz gerekir:

|Uzantı|MIME türü|
|---------------|---------------|
|. manifest|uygulama/bildirim|
|. xaml|uygulama/xaml + xml|
|. Application|uygulama/x-MS-uygulama|
|. xbap|uygulama/x-MS-XBAP|
|. deploy|Uygulama/sekizli-akış|
|. XPS|application/vnd. MS-XpsDocument|

> [!NOTE]
> İstemci sistemlerine MIME türlerini veya dosya uzantılarını kaydetmeniz gerekmez. Microsoft .NET Framework 'Ü yüklediğinizde otomatik olarak kaydedilir.

Aşağıdaki Microsoft Visual Basic Scripting Edition (VBScript) örneği, gerekli MIME türlerini otomatik olarak IIS 'e ekler. Betiği kullanmak için, kodu sunucunuzdaki bir. vbs dosyasına kopyalayın. Ardından, komut satırından dosyayı çalıştırarak veya Microsoft Windows Gezgini 'nde dosyaya çift tıklayarak betiği çalıştırın.

```vb
' This script adds the necessary Windows Presentation Foundation MIME types
' to an IIS Server.
' To use this script, just double-click or execute it from a command line.
' Running this script multiple times results in multiple entries in the IIS MimeMap.

Dim MimeMapObj, MimeMapArray, MimeTypesToAddArray, WshShell, oExec
Const ADS_PROPERTY_UPDATE = 2

' Set the MIME types to be added
MimeTypesToAddArray = Array(".manifest", "application/manifest", ".xaml", _
    "application/xaml+xml", ".application", "application/x-ms-application", _
    ".deploy", "application/octet-stream", ".xbap", "application/x-ms-xbap", _
    ".xps", "application/vnd.ms-xpsdocument")

' Get the MimeMap object
Set MimeMapObj = GetObject("IIS://LocalHost/MimeMap")

' Call AddMimeType for every pair of extension/MIME type
For counter = 0 to UBound(MimeTypesToAddArray) Step 2
    AddMimeType MimeTypesToAddArray(counter), MimeTypesToAddArray(counter+1)
Next

' Create a Shell object
Set WshShell = CreateObject("WScript.Shell")

' Stop and Start the IIS Service
Set oExec = WshShell.Exec("net stop w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = WshShell.Exec("net start w3svc")
Do While oExec.Status = 0
    WScript.Sleep 100
Loop

Set oExec = Nothing

' Report status to user
WScript.Echo "Windows Presentation Foundation MIME types have been registered."

' AddMimeType Sub
Sub AddMimeType (Ext, MType)

    ' Get the mappings from the MimeMap property.
    MimeMapArray = MimeMapObj.GetEx("MimeMap")

    ' Add a new mapping.
    i = UBound(MimeMapArray) + 1
    ReDim Preserve MimeMapArray(i)
    Set MimeMapArray(i) = CreateObject("MimeMap")
    MimeMapArray(i).Extension = Ext
    MimeMapArray(i).MimeType = MType
    MimeMapObj.PutEx ADS_PROPERTY_UPDATE, "MimeMap", MimeMapArray
    MimeMapObj.SetInfo

End Sub
```

> [!NOTE]
> Bu betiği birden çok kez çalıştırmak, Microsoft Internet Information Services (IIS) 5,0 veya Microsoft Internet Information Services (IIS) 6,0 metatabanında birden çok MIME eşleme girişi oluşturur.

Bu betiği çalıştırdıktan sonra, Microsoft Internet Information Services (IIS) 5,0 veya Microsoft Internet Information Services (IIS) 6,0 Microsoft Yönetim Konsolu 'ndan (MMC) ek MIME türleri göremeyebilirsiniz. Ancak, bu MIME türleri Microsoft Internet Information Services (IIS) 5,0 veya Microsoft Internet Information Services (IIS) 6,0 metabase 'e eklenmiştir. Aşağıdaki betik, Microsoft Internet Information Services (IIS) 5,0 veya Microsoft Internet Information Services (IIS) 6,0 metatabanındaki tüm MIME türlerini görüntüler.

```vb
' This script lists the MIME types for an IIS Server.
' To use this script, just double-click or execute it from a command line
' by calling cscript.exe

dim mimeMapEntry, allMimeMaps

' Get the MimeMap object.
Set mimeMapEntry = GetObject("IIS://localhost/MimeMap")
allMimeMaps = mimeMapEntry.GetEx("MimeMap")

' Display the mappings in the table.
For Each mimeMap In allMimeMaps
    WScript.Echo(mimeMap.MimeType & " (" & mimeMap.Extension + ")")
Next
```

Betiği bir `.vbs` dosyası olarak kaydedin (örneğin, `DiscoverIISMimeTypes.vbs`) ve aşağıdaki komutu kullanarak komut isteminden çalıştırın:

```console
cscript DiscoverIISMimeTypes.vbs
```
