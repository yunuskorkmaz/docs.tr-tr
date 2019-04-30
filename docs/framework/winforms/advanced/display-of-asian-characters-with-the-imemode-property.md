---
title: ImeMode Özelliğiyle Asya Karakterlerinin Görüntülenmesi
ms.date: 03/30/2017
helpviewer_keywords:
- Asian languages [Windows Forms], displaying with ImeMode
- Chinese characters [Windows Forms], displaying with ImeMode
- IME mode
- Japanese characters [Windows Forms], displaying with ImeMode
- international applications [Windows Forms], character display
- international characters
- Korean characters
- Asian languages
- Input Method Editor (IME), mode
- localization [Windows Forms], character sets
- globalization [Windows Forms], character sets
ms.assetid: c60ae399-0dab-4f07-9dea-6dbfb15ec0ae
ms.openlocfilehash: 25602e1a878443bd54411dfd6481581abebda5c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755486"
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a><span data-ttu-id="80b01-102">ImeMode Özelliğiyle Asya Karakterlerinin Görüntülenmesi</span><span class="sxs-lookup"><span data-stu-id="80b01-102">Display of Asian Characters with the ImeMode Property</span></span>
<span data-ttu-id="80b01-103"><xref:System.Windows.Forms.Control.ImeMode%2A> Özelliği formlar ve denetimler tarafından Giriş Yöntemi Düzenleyicisi (IME) için belirli bir mod zorlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="80b01-103">The <xref:System.Windows.Forms.Control.ImeMode%2A> property is used by forms and controls to force a specific mode for an input method editor (IME).</span></span> <span data-ttu-id="80b01-104">IME bu yazma sistemleri için normal bir klavye kodlanmış daha fazla karakter olduğundan betikler, Çince, Japonca ve Korece yazı için temel bir bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="80b01-104">The IME is an essential component for writing Chinese, Japanese, and Korean scripts, since these writing systems have more characters than can be encoded for a regular keyboard.</span></span> <span data-ttu-id="80b01-105">Örneğin, yalnızca belirli bir metin kutusunda ASCII karakterlerine izin vermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="80b01-105">For example, you may want to allow only ASCII characters in a particular text box.</span></span> <span data-ttu-id="80b01-106">Böyle bir durumda ayarladığınız <xref:System.Windows.Forms.Control.ImeMode%2A> özelliğini <xref:System.Windows.Forms.ImeMode> ve kullanıcılar yalnızca ASCII karakterler için belirli metin kutusuna girmeniz mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="80b01-106">In such a case you can set the <xref:System.Windows.Forms.Control.ImeMode%2A> property to <xref:System.Windows.Forms.ImeMode> and users will only be able to enter ASCII characters for that particular text box.</span></span> <span data-ttu-id="80b01-107">Varsayılan değer olan <xref:System.Windows.Forms.Control.ImeMode%2A> özelliği <xref:System.Windows.Forms.ImeMode>, formun özelliğini ayarlarsanız, formda tüm denetimler bu ayarı miras alacaktır.</span><span class="sxs-lookup"><span data-stu-id="80b01-107">The default value of the <xref:System.Windows.Forms.Control.ImeMode%2A> property is <xref:System.Windows.Forms.ImeMode>, so if you set the property for a form, all controls on the form will inherit that setting.</span></span> <span data-ttu-id="80b01-108">Daha fazla bilgi için <xref:System.Windows.Forms.Control.ImeMode%2A> ) ve <xref:System.Windows.Forms.ImeMode>.</span><span class="sxs-lookup"><span data-stu-id="80b01-108">For more information, see <xref:System.Windows.Forms.Control.ImeMode%2A> ) and <xref:System.Windows.Forms.ImeMode>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80b01-109">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="80b01-109">See also</span></span>

- [<span data-ttu-id="80b01-110">Windows Forms uygulamaları Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="80b01-110">Globalizing Windows Forms applications</span></span>](globalizing-windows-forms.md)
