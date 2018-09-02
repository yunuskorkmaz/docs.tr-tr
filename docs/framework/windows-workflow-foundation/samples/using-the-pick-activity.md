---
title: Pick etkinliği kullanma
ms.date: 03/30/2017
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
ms.openlocfilehash: 193b60bff7b08c0de9a0957668483eb73be97274
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/01/2018
ms.locfileid: "43452612"
---
# <a name="using-the-pick-activity"></a>Pick etkinliği kullanma
Bu örnek nasıl kullanılacağını gösterir <xref:System.Activities.Statements.Pick> etkinlik.  
  
 <xref:System.Activities.Statements.Pick> Etkinlik, olay tabanlı denetim modelleme sağlar. Benzer şekilde C# davranışını `switch` dalları yalnızca biri yürüten deyimi `switch` deyimi. Farklı `switch` deyimi bir dal yürütüldüğünde bir değere dayalı <xref:System.Activities.Statements.Pick> nasıl bir etkinlik tamamlandıktan sonra bağlı olarak bir dalı etkinliği yürütür.  
  
 Bu örnek, bir kullanıcının belirli bir süre içinde konsolda kişinin adını yazın ister. <xref:System.Activities.Statements.Pick> Örnek etkinlik tabanlı olup kullanıcı adında 5 saniye içinde veya türleri üzerinde yürütülen iki dal vardır. Kullanıcı 5 saniye içinde adında yazarsa, ilk dalı, bir özel içeren yürütülür `ReadLine` etkinlik; Aksi durumda diğer dal, içeren yürütülen bir <xref:System.Activities.Statements.Delay> etkinlik. Bir kullanıcının adını konsolda yazılmış sonra kullanıcının adını konsolda yazdırılır. Giriş 5 saniye içinde girilmezse, işlemi zaman aşımına uğradı.  
  
## <a name="demonstrates"></a>Gösteriler  
 <xref:System.Activities.Statements.Pick> Etkinlik.  
  
## <a name="discussion"></a>Tartışma  
 Bir tasarımcı iş akışı ve kodlanmış iş akışı örneği içerir.  
  
 Tasarımcı iş akışı  
 Bir iş akışı Tasarımcısı'nda oluşturma Tasarımcısı sürümünü gösterir. Aşağıdaki dosyalar dahil edilir:  
  
-   Program.cs: İçerir `Main` örnek iş akışı yürüten işlev.  
  
-   ReadString.cs: bazı giriş konsoldan okuyan özel bir etkinlik.  
  
-   Sequence1.XAML: kullandığı çekme Tasarımcı kullanılarak oluşturulmuş bir iş akışı.  
  
 Kodlanmış bir iş akışı  
 Bir iş akışı Tasarımcısı'nda oluşturma kodlanmış sürümünü gösterir. Aşağıdaki dosyalar dahil edilir:  
  
-   Program.cs: İçerir `Main` örnek iş akışı yürüten işlev.  
  
-   ReadString.cs: bazı giriş konsoldan okuyan özel bir etkinlik.  
  
#### <a name="to-use-this-sample"></a>Bu örneği kullanmak için  
  
1.  Kullanarak [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], Pick.sln çözüm dosyasını açın.  
  
2.  Çözümü derlemek için CTRL + SHIFT + B tuşlarına basın.  
  
3.  Çözümü çalıştırmak için F5 tuşuna basın.  
  
> [!IMPORTANT]
>  Örnekler, makinenizde zaten yüklü. Devam etmeden önce şu (varsayılan) dizin denetleyin.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Bu dizin mevcut değilse Git [Windows Communication Foundation (WCF) ve .NET Framework 4 için Windows Workflow Foundation (WF) örnekleri](https://go.microsoft.com/fwlink/?LinkId=150780) tüm Windows Communication Foundation (WCF) indirmek için ve [!INCLUDE[wf1](../../../../includes/wf1-md.md)] örnekleri. Bu örnek, şu dizinde bulunur.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`