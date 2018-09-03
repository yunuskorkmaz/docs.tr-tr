---
title: Bir .NET Framework 4.5 iş akışında .NET Framework 3.0 veya .NET Framework 3.5 etkinliği kullanma
ms.date: 03/30/2017
ms.assetid: 6c53fd4c-5dd0-4fb4-ab6b-111302629548
ms.openlocfilehash: ec44e56a99660ba422c73bbbf00bf5ef6b7b61ff
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486137"
---
# <a name="using-a-net-framework-30-or-net-framework-35-activity-in-a-net-framework-45-workflow"></a>Bir .NET Framework 4.5 iş akışında .NET Framework 3.0 veya .NET Framework 3.5 etkinliği kullanma
<xref:System.Activities.Statements.Interop> Etkinliği sağlar, bir .NET Framework 3.0 Windows Workflow Foundation (WF) etkinliği içinde çalıştırmak bir [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] iş akışı. Bu örnek nasıl kullanılacağını gösterir <xref:System.Activities.Statements.Interop> bir dize, özel bir bağımsız değişken olarak geçirmek için etkinlik [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] etkinlik.  
  
## <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], SimpleInterop.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için CTRL + F5 tuşlarına basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Migration\SimpleInterop`  
  
## <a name="see-also"></a>Ayrıca Bkz.
