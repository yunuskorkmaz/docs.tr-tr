---
title: İleti Kuyruğa Alma Yükleme (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 42e66029f8538877ded424f72cb6c829444d1ee0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935987"
---
# <a name="installing-message-queuing-msmq"></a>İleti Kuyruğa Alma Yükleme (MSMQ)
Aşağıdaki yordamlarda Message Queuing 4,0 ve Message Queuing 3,0 ' nin nasıl yükleneceği gösterilmektedir.  
  
> [!NOTE]
> Message Queuing 4,0, ve [!INCLUDE[wxp](../../../../includes/wxp-md.md)] [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]' de kullanılamaz.  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>Message Queuing 4,0 ' i Windows Server 2008 veya Windows Server 2008 R2 'ye yüklemek için  
  
1. Sunucu Yöneticisi, **Özellikler**' e tıklayın.  
  
2. Sağ bölmedeki **Özellikler Özeti**' ne tıklayın, **Özellik Ekle**' ye tıklayın.  
  
3. Ortaya çıkan pencerede **Message Queuing**' ı genişletin.  
  
4. **Message Queuing Hizmetleri**' ni genişletin.  
  
5. **Dizin Hizmetleri Tümleştirme** (bir etki alanına katılmış bilgisayarlar için) öğesine tıklayın ve ardından **http desteği**' ne tıklayın.  
  
6. **İleri**' ye ve ardından **Install**' a tıklayın.  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>Windows 7 veya Windows Vista 'da Message Queuing 4,0 yüklemek için  
  
1. **Denetim Masası**'nı açın.  
  
2. **Programlar** ' a ve ardından **Programlar ve Özellikler**' ın altında, **Windows özelliklerini aç ve Kapat**' a tıklayın.  
  
3. Microsoft Message Queue (MSMQ) sunucusu ' nu genişletin, Microsoft Message Queue (MSMQ) Server Core ' u genişletin ve ardından yüklemek üzere aşağıdaki Message Queuing Özellikler onay kutularını seçin:  
  
    - MSMQ Active Directory Domain Services Tümleştirme (bir etki alanına katılmış bilgisayarlar için).  
  
    - MSMQ HTTP desteği.  
  
4. **Tamam**'ı tıklatın.  
  
5. Bilgisayarı yeniden başlatmanız istenirse, yüklemeyi gerçekleştirmek için **Tamam** ' ı tıklatın.  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>Message Queuing 3,0 ' i Windows XP ve Windows Server 2003 ' ye yüklemek için  
  
1. **Denetim Masası**'nı açın.  
  
2. **Program Ekle Kaldır** ' a ve ardından **Windows Bileşenleri Ekle**' ye tıklayın.  
  
3. Message Queuing seçin ve **Ayrıntılar**' a tıklayın.  
  
    > [!NOTE]
    >  Çalıştırıyorsanız [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Message Queuing erişmek için uygulama sunucusu ' nu seçin.  
  
4. Ayrıntılar sayfasında MSMQ HTTP desteği seçeneğinin seçildiğinden emin olun.  
  
5. Ayrıntılar sayfasından çıkmak için **Tamam** ' ı tıklatın ve ardından **İleri**' yi tıklatın. Yüklemeyi tamamlayın.  
  
6. Bilgisayarı yeniden başlatmanız istenirse, yüklemeyi gerçekleştirmek için **Tamam** ' ı tıklatın.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurulum Yönergeleri](../../../../docs/framework/wcf/samples/set-up-instructions.md)
