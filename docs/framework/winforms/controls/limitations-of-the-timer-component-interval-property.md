---
title: Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar
ms.date: 03/30/2017
helpviewer_keywords:
- timers [Windows Forms], event intervals
- Interval property [Windows Forms], limitations
- timers [Windows Forms], Windows-based
- Timer component [Windows Forms], limitations of Interval property
ms.assetid: 7e5fb513-77e7-4046-a8e8-aab94e61ca0f
ms.openlocfilehash: a9c4fda179e45ad2cf2ee2183e5881e97b763cdc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64644937"
---
# <a name="limitations-of-the-windows-forms-timer-components-interval-property"></a><span data-ttu-id="abd83-102">Windows Forms Süreölçer Bileşeninin Aralık Özelliğiyle İlgili Sınırlamalar</span><span class="sxs-lookup"><span data-stu-id="abd83-102">Limitations of the Windows Forms Timer Component's Interval Property</span></span>
<span data-ttu-id="abd83-103">Windows Forms <xref:System.Windows.Forms.Timer> bileşeniyse bir <xref:System.Windows.Forms.Timer.Interval%2A> özelliği bir süreölçer olayı ve sonraki arasında geçen milisaniye sayısını belirtir.</span><span class="sxs-lookup"><span data-stu-id="abd83-103">The Windows Forms <xref:System.Windows.Forms.Timer> component has an <xref:System.Windows.Forms.Timer.Interval%2A> property that specifies the number of milliseconds that pass between one timer event and the next.</span></span> <span data-ttu-id="abd83-104">Bileşen devre dışı bırakılmadığı sürece, bir zamanlayıcı almaya devam ettiğinden <xref:System.Windows.Forms.Timer.Tick> zaman kabaca eşit aralıklarla olay.</span><span class="sxs-lookup"><span data-stu-id="abd83-104">Unless the component is disabled, a timer continues to receive the <xref:System.Windows.Forms.Timer.Tick> event at roughly equal intervals of time.</span></span>  
  
 <span data-ttu-id="abd83-105">Bu bileşen, bir Windows Forms ortamı için tasarlanmıştır.</span><span class="sxs-lookup"><span data-stu-id="abd83-105">This component is designed for a Windows Forms environment.</span></span> <span data-ttu-id="abd83-106">Bir sunucu ortamı için uygun olan bir zamanlayıcı gerekirse bkz [sunucu tabanlı zamanlayıcılar giriş](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="abd83-106">If you need a timer that is suitable for a server environment, see [Introduction to Server-Based Timers](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2008/tb9yt5e6(v=vs.90)).</span></span>  
  
## <a name="the-interval-property"></a><span data-ttu-id="abd83-107">Aralık özelliği</span><span class="sxs-lookup"><span data-stu-id="abd83-107">The Interval Property</span></span>  
 <span data-ttu-id="abd83-108"><xref:System.Windows.Forms.Timer.Interval%2A> Özelliğine sahip olduğunda programlama dikkate alınması gereken bazı sınırlamalar bir <xref:System.Windows.Forms.Timer> bileşeni:</span><span class="sxs-lookup"><span data-stu-id="abd83-108">The <xref:System.Windows.Forms.Timer.Interval%2A> property has a few limitations to consider when you are programming a <xref:System.Windows.Forms.Timer> component:</span></span>  
  
- <span data-ttu-id="abd83-109">Uygulamanızı veya başka bir uygulama sistem üzerinde ağır taleplerini değiştirirken, — uzun döngüleri, yoğun hesaplama veya sürücü, ağ veya bağlantı noktası erişim gibi — uygulamanızı Zamanlayıcı olaylar çok sık olarak alamayabilir <xref:System.Windows.Forms.Timer.Interval%2A> özelliği belirtir.</span><span class="sxs-lookup"><span data-stu-id="abd83-109">If your application or another application is making heavy demands on the system — such as long loops, intensive calculations, or drive, network, or port access — your application may not get timer events as often as the <xref:System.Windows.Forms.Timer.Interval%2A> property specifies.</span></span>  
  
- <span data-ttu-id="abd83-110">Aralık tam zamanında geçmesi garanti edilmez.</span><span class="sxs-lookup"><span data-stu-id="abd83-110">The interval is not guaranteed to elapse exactly on time.</span></span> <span data-ttu-id="abd83-111">Doğruluğunu sağlamak için Zamanlayıcıyı gerektiği gibi sistem saati denetlemek yerine biriken zaman dahili olarak izlemek deneyin.</span><span class="sxs-lookup"><span data-stu-id="abd83-111">To ensure accuracy, the timer should check the system clock as needed, rather than try to keep track of accumulated time internally.</span></span>  
  
- <span data-ttu-id="abd83-112">Duyarlığını <xref:System.Windows.Forms.Timer.Interval%2A> milisaniye cinsinden bir özelliktir.</span><span class="sxs-lookup"><span data-stu-id="abd83-112">The precision of the <xref:System.Windows.Forms.Timer.Interval%2A> property is in milliseconds.</span></span> <span data-ttu-id="abd83-113">Bazı bilgisayarlar, bir milisaniyeden daha yüksek çözünürlüğe sahip yüksek çözünürlüklü bir sayaç belirtin.</span><span class="sxs-lookup"><span data-stu-id="abd83-113">Some computers provide a high-resolution counter that has a resolution higher than milliseconds.</span></span> <span data-ttu-id="abd83-114">Böyle bir sayaç kullanılabilirliğini bilgisayarınızın işlemci donanımda bağlıdır.</span><span class="sxs-lookup"><span data-stu-id="abd83-114">The availability of such a counter depends on the processor hardware of your computer.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="abd83-115">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="abd83-115">See also</span></span>

- <xref:System.Windows.Forms.Timer>
- [<span data-ttu-id="abd83-116">Süreölçer Bileşeni</span><span class="sxs-lookup"><span data-stu-id="abd83-116">Timer Component</span></span>](timer-component-windows-forms.md)
- [<span data-ttu-id="abd83-117">Süreölçer Bileşenine Genel Bakış</span><span class="sxs-lookup"><span data-stu-id="abd83-117">Timer Component Overview</span></span>](timer-component-overview-windows-forms.md)
