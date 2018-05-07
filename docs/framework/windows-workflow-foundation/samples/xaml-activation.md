---
title: XAML etkinleştirme
ms.date: 03/30/2017
ms.assetid: 486760e2-bb10-4ed5-8c02-fe7472498d2d
ms.openlocfilehash: 8621b0ea7b390c81e76ac7eeedb0b547b44320d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 05/04/2018
---
# <a name="xaml-activation"></a>XAML etkinleştirme
Bu örnek, IIS'de bildirim temelli bir iş akışı barındırma gösterilmiştir. Örnek olarak adlandırılan bir temel iş akışıdır `EchoService` bir işleme sahip.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü olabilir. Devam etmeden önce aşağıdaki (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse (indirme) gidin tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek aşağıdaki dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\XAMLActivation`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Ayarlamak için derleme ve örnek çalıştırın  
  
1.  XAMLActivation.sln çözümde açmak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Tuşlarına basarak çözümü oluşturun **F5**.  
  
3.  WcfTestClient.exe çalıştırın. Bir komut isteminden aşağıdaki komutu yazın:  
  
    1.  CD %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE  
  
    2.  WcfTestClient.exe çalıştırın.  
  
4.  CTRL + SHIFT + A tuşuna basarak ve hizmeti adresi ayarını üzerinde WcfTestClient.exe hizmetinin adresini ayarlamak http://localhost:56133/Service.xamlx.  
  
5.  Hizmeti sınamak için Yankı işlemi gerçekleştirin.  
  
6.  Hizmeti IIS DeployToIIS.Bat yönetici ayrıcalıklarıyla bir komut istemi kullanarak dağıtın.  
  
7.  İstemciye hizmet adresi güncelleştirme http://localhost/XAMLActivation/Service.xamlx ve hizmeti yeniden WcfTestClient.exe kullanarak test.
