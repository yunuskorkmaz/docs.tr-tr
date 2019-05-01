---
title: 'Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma'
ms.date: 03/30/2017
helpviewer_keywords:
- HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
ms.openlocfilehash: 2677c57c825675c884d057827e065f05d7c8bf30
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62039149"
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a>Nasıl yapılır: WCF Etkinleştirme Bileşenlerini Yükleme ve Yapılandırma
Bu konuda Windows İşlem Etkinleştirme Hizmeti (WAS olarak da bilinir) ' için gereken adımları açıklar [!INCLUDE[wv](../../../../includes/wv-md.md)] Windows Communication Foundation (WCF) barındırmak için HTTP üzerinden iletişim kurmazlar Hizmetleri protokolleri ağ. Aşağıdaki bölümlerde, bu yapılandırmanın adımları özetlemektedir:  
  
- Yükleme (veya yüklenmesini onaylayın) WCF etkinleştirme bileşenlerini.  
  
- WAS olmayan HTTP protokolü destekleyecek şekilde yapılandırın. Aşağıdaki yordam yapılandırır [!INCLUDE[wv](../../../../includes/wv-md.md)] TCP Etkinleştirmesi için.  
  
 Yükleme ve yapılandırma WAS gördükten sonra [nasıl yapılır: Was'ta WCF Hizmeti barındırma](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) yordamları WAS kullanan bir HTTP olmayan uç noktasını kullanıma sunan bir WCF hizmeti oluşturma.  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a>WCF HTTP olmayan etkinleştirme bileşenlerini yükleme  
  
1. Tıklayın **Başlat** düğmesine ve ardından **Denetim Masası**.  
  
2. Tıklayın **programlar**ve ardından **programlar ve Özellikler**.  
  
3. Üzerinde **görevleri** menüsünde tıklatın **kapatma Windows özelliklerini aç veya Kapat**.  
  
4. Bulma [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] düğümünü seçin ve genişletin.  
  
5. Seçin **WCF Http olmayan etkinleştirme bileşenlerini** kutusuna ve bu ayarı kaydedin.  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a>WAS TCP etkinleştirilmesini destekleyecek şekilde yapılandırmak için  
  
1. NET.TCP etkinleştirmeyi desteklemek için varsayılan Web sitesi ilk net.tcp bağlantı noktasına bağlı olmalıdır. İle birlikte yüklenen Appcmd.exe kullanarak bunu yapabilirsiniz [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Yönetimi araç. Bir yönetici düzeyinde komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  Tek metin satırı komutudur. Bu komut, varsayılan Web sitesine herhangi bir ana bilgisayar adı ile 808 numaralı TCP bağlantı noktasını dinleyen bir net.tcp site bağlaması ekler.  
  
2. Bir sitedeki tüm uygulamaları genel net.tcp bağlama paylaşsa da her uygulama net.tcp destek ayrı ayrı etkinleştirebilirsiniz. Uygulama için NET.TCP etkinleştirmek için bir yönetici düzeyinde komut isteminden aşağıdaki komutu çalıştırın.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  Tek metin satırı komutudur. Bu komut etkinleştirir /\<*WCF uygulaması*> her ikisi de kullanılarak erişilecektir uygulama `http://localhost/<WCF Application>` ve `net.tcp://localhost/<WCF Application>`.
  
     Eklediğiniz net.tcp site bağlaması için bu örnek kaldırın.  
  
     Bir kolaylık olarak örnek dizinde yer RemoveNetTcpSiteBinding.cmd adlı bir toplu iş dosyasında aşağıdaki iki adımı uygulanır.  
  
    1. NET.TCP, bir yönetici düzeyinde komut istemi penceresinde aşağıdaki komutu çalıştırarak etkin protokoller listesinden kaldırın.  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  Tek metin satırı komutudur.  
  
    2. Net.tcp site bağlaması, yükseltilmiş bir komut istemi penceresinde aşağıdaki komutu çalıştırarak kaldırın:  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  Tek metin satırı komutudur.  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a>NET.TCP etkin protokoller listesinden kaldırmak için  
  
1. NET.TCP etkin protokoller listesinden kaldırmak için bir yönetici düzeyinde komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  Tek metin satırı komutudur.  
  
### <a name="to-remove-the-nettcp-site-binding"></a>Net.tcp site bağlaması kaldırmak için  
  
1. Bağlama net.tcp siteyi kaldırmak için bir yönetici düzeyinde komut istemi penceresinde aşağıdaki komutu çalıştırın.  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  Tek metin satırı komutudur.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [TCP Etkinleştirme](../../../../docs/framework/wcf/samples/tcp-activation.md)
- [MSMQ Etkinleştirme](../../../../docs/framework/wcf/samples/msmq-activation.md)
- [NamedPipe Etkinleştirme](../../../../docs/framework/wcf/samples/namedpipe-activation.md)
- [Windows Server App Fabric barındırma özellikleri](https://go.microsoft.com/fwlink/?LinkId=201276)
