---
title: "ImeMode Özelliğiyle Asya Karakterlerinin Görüntülenmesi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5971fd9a75f936d2ec63eea6a086c681ec996652
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="display-of-asian-characters-with-the-imemode-property"></a><span data-ttu-id="d5a0f-102">ImeMode Özelliğiyle Asya Karakterlerinin Görüntülenmesi</span><span class="sxs-lookup"><span data-stu-id="d5a0f-102">Display of Asian Characters with the ImeMode Property</span></span>
<span data-ttu-id="d5a0f-103"><xref:System.Windows.Forms.Control.ImeMode%2A> Özelliği formlar ve denetimler tarafından bir Giriş Yöntemi Düzenleyicisi (IME) için belirli bir mod zorlamak için kullanılır.</span><span class="sxs-lookup"><span data-stu-id="d5a0f-103">The <xref:System.Windows.Forms.Control.ImeMode%2A> property is used by forms and controls to force a specific mode for an input method editor (IME).</span></span> <span data-ttu-id="d5a0f-104">IME bu yazı sistemleri karakterlerden için normal bir klavye olarak kodlanmış daha fazlasına sahip olduğundan, Çince, Japonca ve Korece komut dosyaları yazmak için temel bir bileşenidir.</span><span class="sxs-lookup"><span data-stu-id="d5a0f-104">The IME is an essential component for writing Chinese, Japanese, and Korean scripts, since these writing systems have more characters than can be encoded for a regular keyboard.</span></span> <span data-ttu-id="d5a0f-105">Örneğin, yalnızca ASCII karakterleri belirli metin kutusunda izin vermek isteyebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="d5a0f-105">For example, you may want to allow only ASCII characters in a particular text box.</span></span> <span data-ttu-id="d5a0f-106">Böyle bir durumda ayarladığınız <xref:System.Windows.Forms.Control.ImeMode%2A> özelliğine <xref:System.Windows.Forms.ImeMode> ve kullanıcıların yalnızca ASCII karakterler için belirli metin kutusuna girmeniz mümkün olacaktır.</span><span class="sxs-lookup"><span data-stu-id="d5a0f-106">In such a case you can set the <xref:System.Windows.Forms.Control.ImeMode%2A> property to <xref:System.Windows.Forms.ImeMode> and users will only be able to enter ASCII characters for that particular text box.</span></span> <span data-ttu-id="d5a0f-107">Varsayılan değer olan <xref:System.Windows.Forms.Control.ImeMode%2A> özelliği <xref:System.Windows.Forms.ImeMode>, bu özellik için bir form ayarlarsanız, formdaki tüm denetimler bu ayarı devralır.</span><span class="sxs-lookup"><span data-stu-id="d5a0f-107">The default value of the <xref:System.Windows.Forms.Control.ImeMode%2A> property is <xref:System.Windows.Forms.ImeMode>, so if you set the property for a form, all controls on the form will inherit that setting.</span></span> <span data-ttu-id="d5a0f-108">Daha fazla bilgi için bkz: <xref:System.Windows.Forms.Control.ImeMode%2A> ) ve <xref:System.Windows.Forms.ImeMode>.</span><span class="sxs-lookup"><span data-stu-id="d5a0f-108">For more information, see <xref:System.Windows.Forms.Control.ImeMode%2A> ) and <xref:System.Windows.Forms.ImeMode>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5a0f-109">Ayrıca Bkz.</span><span class="sxs-lookup"><span data-stu-id="d5a0f-109">See Also</span></span>  
 [<span data-ttu-id="d5a0f-110">Windows Forms’u Genelleştirme</span><span class="sxs-lookup"><span data-stu-id="d5a0f-110">Globalizing Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/globalizing-windows-forms.md)
