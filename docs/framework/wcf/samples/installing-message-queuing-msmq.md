---
title: İleti Kuyruğa Alma Yükleme (MSMQ)
ms.date: 03/30/2017
ms.assetid: 7ddcd497-3e04-427e-bc04-3610ad98b01e
ms.openlocfilehash: 813de350c3fd32bb4698384d6b770af8a0913739
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648339"
---
# <a name="installing-message-queuing-msmq"></a>İleti Kuyruğa Alma Yükleme (MSMQ)
Aşağıdaki yordamlar, Message Queuing 4.0 ve Message Queuing 3.0 nasıl yükleneceğini gösterir.  
  
> [!NOTE]
>  Message Queuing 4.0 kullanılabilir değil [!INCLUDE[wxp](../../../../includes/wxp-md.md)] ve [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
#### <a name="to-install-message-queuing-40-on-windows-server-2008-or-windows-server-2008-r2"></a>Message Queuing 4.0, Windows Server 2008 veya Windows Server 2008 R2 üzerinde yükleme için  
  
1. Sunucu Yöneticisi'nde **özellikleri**.  
  
2. Sağ bölmede **özellikler özeti**, tıklayın **Özellik Ekle**.  
  
3. Sonuçta elde edilen penceresinde **Message Queuing**.  
  
4. Genişletin **Message Queuing Hizmetleri**.  
  
5. Tıklayın **Dizin Hizmetleri Tümleştirme** (bir etki alanına katılmış bilgisayarlar için),'ı **HTTP desteği**.  
  
6. Tıklayın **sonraki**, ardından **yükleme**.  
  
#### <a name="to-install-message-queuing-40-on-windows-7-or-windows-vista"></a>Message Queuing 4.0, Windows 7 veya Windows Vista'yı yüklemek için  
  
1. **Denetim Masası**'nı açın.  
  
2. Tıklayın **programlar** ve sonra **programlar ve Özellikler**, tıklayın **Windows özelliklerini açma ve kapatma**.  
  
3. Microsoft Message Queue (MSMQ) sunucusunu genişletin, Microsoft Message Queue (MSMQ) Sunucu Çekirdeği'ni genişletin ve sonra yüklemek aşağıdaki olan Message Queuing özellikler için onay kutularını seçin:  
  
    - MSMQ Active Directory etki alanı Hizmetleri Tümleştirme (bir etki alanına katılmış bilgisayarlar için).  
  
    - MSMQ HTTP desteği.  
  
4. **Tamam**'ı tıklatın.  
  
5. Bilgisayarı yeniden başlatmanız istenirse, tıklayın **Tamam** yüklemeyi tamamlamak için.  
  
#### <a name="to-install-message-queuing-30-on-windows-xp-and-windows-server-2003"></a>Message Queuing 3.0, Windows XP ve Windows Server 2003'te yüklemek için  
  
1. **Denetim Masası**'nı açın.  
  
2. Tıklayın **Program Ekle/Kaldır** ve ardından **Windows BileşenleriEkle/**.  
  
3. Message Queuing seçip tıklayın **ayrıntıları**.  
  
    > [!NOTE]
    >  Çalıştırıyorsanız [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Message Queuing erişmek için uygulama sunucusu seçin.  
  
4. MSMQ HTTP desteği, Ayrıntılar sayfasında belirlenen seçenek emin olun.  
  
5. Tıklayın **Tamam** Ayrıntılar sayfası çıkın ve ardından **sonraki**. Yüklemeyi tamamlayın.  
  
6. Bilgisayarı yeniden başlatmanız istenirse, tıklayın **Tamam** yüklemeyi tamamlamak için.  
  
## <a name="see-also"></a>Ayrıca bkz.

- [Kurulum Yönergeleri](../../../../docs/framework/wcf/samples/set-up-instructions.md)
