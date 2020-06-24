---
title: 'Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma'
description: Windows Vista 'da, HTTP üzerinden iletişim kurmayan WCF hizmetlerini barındırmak için Windows Işlem etkinleştirme hizmeti 'ni (WAS) ayarlamayı öğrenin.
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 84a0dcc4fed28ebd7a536bdabfcdc389be6072d8
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246889"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma

Bu konuda, Windows Vista 'da HTTP ağ protokolleri üzerinden iletişim kurmayan Windows Communication Foundation (WCF) hizmetlerini barındırmak için Windows Işlem etkinleştirme hizmeti 'ni (WAS olarak da bilinir) ayarlamak için gereken adımlar açıklanmaktadır. Aşağıdaki bölümlerde bu yapılandırma için adımlar ana hatlarıyla verilmiştir:

- WCF etkinleştirme bileşenlerini yükleme (veya yüklemesini onaylama).

- ' İ HTTP olmayan bir protokolü destekleyecek şekilde yapılandırın. Aşağıdaki yordam, TCP Etkinleştirmesi için Windows Vista 'Yı yapılandırır.

WAS 'yi yükledikten ve yapılandırdıktan sonra, ile ilgili HTTP olmayan bir uç nokta sunan bir WCF hizmeti oluşturma yordamları için bkz. [nasıl yapılır: ' de BIR WCF hizmetini barındırma](how-to-host-a-wcf-service-in-was.md) .

## <a name="to-install-the-wcf-non-http-activation-components"></a>WCF HTTP olmayan etkinleştirme bileşenlerini yüklemek için

1. **Başlat** düğmesine tıklayın ve ardından **Denetim Masası**' na tıklayın.

2. **Programlar**' a ve ardından **Programlar ve Özellikler**' e tıklayın.

3. **Görevler** menüsünde, **Windows özelliklerini aç veya kapat**' a tıklayın.

4. WinFX düğümünü bulun, seçin ve genişletin.

5. **WCF HTTP olmayan etkinleştirme bileşenleri** kutusunu seçin ve ayarı kaydedin.

## <a name="to-configure-the-was-to-support-tcp-activation"></a>Yapılandırmasını TCP etkinleştirmesini destekleyecek şekilde yapılandırmak için

1. Net. TCP etkinleştirmesini desteklemek için, önce varsayılan Web sitesinin bir net. TCP bağlantı noktasına bağlanması gerekir. Bunu, IIS 7,0 yönetim araç takımı ile yüklenen Appcmd.exe kullanarak yapabilirsiniz. Yönetici düzeyinde bir komut Istemi penceresinde aşağıdaki komutu çalıştırın.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > Bu komut, tek satırlık bir metin. Bu komut, TCP bağlantı noktası 808 ' de dinleme yapan varsayılan Web sitesine bir net. TCP site bağlaması ekleyerek herhangi bir ana bilgisayar adı ekler.

2. Bir sitedeki tüm uygulamalar ortak bir net. TCP bağlamasını paylaşır, ancak her uygulama net. TCP desteğini tek tek etkinleştirebilir. Uygulama için net. TCP 'yi etkinleştirmek üzere yönetici düzeyinde bir komut isteminden aşağıdaki komutu çalıştırın.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp
    ```

    > [!NOTE]
    > Bu komut, tek satırlık bir metin. Bu komut,/ \<*WCF Application*> uygulamasına hem hem de kullanılarak erişilmesini sağlar `http://localhost/<WCF Application>` `net.tcp://localhost/<WCF Application>` .

     Bu örnek için eklemiş olduğunuz net. TCP site bağlamasını kaldırın.

     Kolaylık olması halinde, örnek dizinde bulunan RemoveNetTcpSiteBinding. cmd adlı bir toplu iş dosyasında aşağıdaki iki adım uygulanır.

    1. Yönetici düzeyinde bir komut Istemi penceresinde aşağıdaki komutu çalıştırarak, etkin protokoller listesinden net. TCP ' i kaldırın.

        ```console
        %windir%\system32\inetsrv\appcmd.exe set app
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
        ```

        > [!NOTE]
        > Bu komut, tek satırlık bir metin.

    2. Yükseltilmiş bir komut Istemi penceresinde aşağıdaki komutu çalıştırarak net. TCP site bağlamasını kaldırın:

        ```console
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
        --bindings.[protocol='net.tcp',bindingInformation='808:*']
        ```

        > [!NOTE]
        > Bu komut, tek satırlık bir metin.

## <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a>Etkin protokoller listesinden net. TCP 'yi kaldırmak için

1. Etkin protokoller listesinden net. TCP ' yi kaldırmak için, yönetici düzeyinde bir komut Istemi penceresinde aşağıdaki komutu çalıştırın.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http
    ```

    > [!NOTE]
    > Bu komut, tek satırlık bir metin.

## <a name="to-remove-the-nettcp-site-binding"></a>Net. TCP site bağlamasını kaldırmak için

1. Net. TCP site bağlamasını kaldırmak için aşağıdaki komutu yönetici düzeyinde bir komut Istemi penceresinde çalıştırın.

    ```console
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"
    -bindings.[protocol='net.tcp',bindingInformation='808:*']
    ```

    > [!NOTE]
    > Bu komut, tek satırlık bir metin.

## <a name="see-also"></a>Ayrıca bkz.

- [TCP Etkinleştirme](../samples/tcp-activation.md)
- [MSMQ Etkinleştirme](../samples/msmq-activation.md)
- [NamedPipe Etkinleştirme](../samples/namedpipe-activation.md)
- [Windows Server App Fabric barındırma özellikleri](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
