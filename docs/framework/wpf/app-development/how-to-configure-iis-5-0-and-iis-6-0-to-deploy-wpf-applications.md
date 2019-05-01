---
title: "Nasıl yapılır: WPF Uygulamalarını Dağıtmak için IIS 5.0 ve IIS 6.0'ı Yapılandırma"
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
ms.openlocfilehash: 6fa00c4ced8c05d056703560e5740689c6dcfe39
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61981461"
---
# <a name="how-to-configure-iis-50-and-iis-60-to-deploy-wpf-applications"></a>Nasıl yapılır: WPF Uygulamalarını Dağıtmak için IIS 5.0 ve IIS 6.0'ı Yapılandırma

Dağıtabileceğiniz bir [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] uygun ile yapılandırılmış olduğu sürece uygulama çoğu Web sunucularından [!INCLUDE[TLA#tla_mime](../../../../includes/tlasharptla-mime-md.md)] türleri. Varsayılan olarak, [!INCLUDE[TLA#tla_iis70](../../../../includes/tlasharptla-iis70-md.md)] ile yapılandırılmıştır [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] türleri, ancak [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ve [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] değil.

Bu konu nasıl yapılandırılacağını açıklar [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] ve [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] dağıtmak için [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uygulamalar.

> [!NOTE]
> Denetleyebilirsiniz *UserAgent* bir sistemi .NET Framework'ün yüklü olup olmadığını belirlemek için kayıt defterinde dize. Ayrıntılar ve inceleyen bir betik *UserAgent* .NET Framework sistem üzerinde yüklü olup olmadığını belirlemek için bkz: dize [algılamak yüklü olup olmadığı .NET Framework 3.0](how-to-detect-whether-the-net-framework-3-0-is-installed.md).

<a name="content_expiration"></a>

## <a name="adjust-the-content-expiration-setting"></a>İçerik sona erme ayarını yapma

1 dakika içerik sona erme ayarını değiştirmeniz gerekir. Aşağıdaki yordamı ile bunun nasıl yapılacağını açıklar [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)].

1. Tıklayın **Başlat** menüsünde **Yönetimsel Araçlar**, tıklatıp **Internet Information Services (IIS) Yöneticisi'ni**. Bu uygulama "% SystemRoot%\system32\inetsrv\iis.msc" ile komut satırından da başlatabilirsiniz.

2. Genişletin [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)] bulana kadar ağaç **varsayılan Web sitesi** düğümü.

3. Sağ **varsayılan Web sitesi** seçip **özellikleri** bağlam menüsünden.

4. Seçin **HTTP üstbilgileri** sekmesi ve "İçerik sona erme tarihini etkinleştir"'a tıklayın.

5. 1 dakika sonra süresi dolacak şekilde içeriği ayarlayın.

<a name="register_mime_types"></a>

## <a name="register-mime-types-and-file-extensions"></a>Kayıt MIME türleri ve dosya uzantıları

Birkaç kaydetmelisiniz [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] türleri ve dosya uzantıları böylece İstemci sisteminde tarayıcı doğru işleyici yükleyebilir. Aşağıdaki türleri eklemeniz gerekir:

|Dahili numara|MIME türü|
|---------------|---------------|
|.manifest|Uygulama/bildirimi|
|.xaml|Uygulama/xaml + xml şeklindedir|
|.Application|Application/x-ms-uygulama|
|.xbap|Application/x-ms-xbap|
|.deploy|Uygulama/octet-akış|
|.XPS|Uygulama/vnd.ms-xpsdocument|

> [!NOTE]
> Kaydedilecek gerekmez [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] türleri veya istemci sistemlerine dosya uzantıları. Microsoft .NET Framework'ı yüklediğinizde otomatik olarak kaydedilir.

Aşağıdaki Microsoft Visual Basic Scripting Edition (VBScript) örnek otomatik olarak gerekli ekler [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] türlerine [!INCLUDE[TLA2#tla_iis5](../../../../includes/tla2sharptla-iis5-md.md)]. Betiği kullanmak için kodu sunucunuzda .vbs dosyasına kopyalayın. Ardından, dosyayı komut satırından çalıştırma ya da dosyasına çift betiği çalıştırmak [!INCLUDE[TLA#tla_winexpl](../../../../includes/tlasharptla-winexpl-md.md)].

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
> Bu betik, birden çok kez çalıştıran birden çok oluşturur [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] eşleme girişi [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] veya [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metatabanı.

Bu betiği çalıştırdıktan sonra ek göremeyebilirsiniz [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] gelen türleri [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] veya [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] [!INCLUDE[TLA#tla_mmc](../../../../includes/tlasharptla-mmc-md.md)]. Ancak, bunlar [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] türleri eklenmiştir [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] veya [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metatabanı. Aşağıdaki betiği tüm görüntüler [!INCLUDE[TLA2#tla_mime](../../../../includes/tla2sharptla-mime-md.md)] türlerini [!INCLUDE[TLA#tla_iis50](../../../../includes/tlasharptla-iis50-md.md)] veya [!INCLUDE[TLA#tla_iis60](../../../../includes/tlasharptla-iis60-md.md)] metatabanı.

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

Betik olarak Kaydet bir `.vbs` dosya (örneğin, `DiscoverIISMimeTypes.vbs`) ve aşağıdaki komutu kullanarak komut isteminden çalıştırın:

```console
cscript DiscoverIISMimeTypes.vbs
```
