---
title: "Grafik Kapsayıcıları Kullanma"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 244f8e8a280369798daf12f8a61519826f937a4a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/22/2017
---
# <a name="using-graphics-containers"></a>Grafik Kapsayıcıları Kullanma
A <xref:System.Drawing.Graphics> nesnesi sağlar yöntemleri gibi <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, ve <xref:System.Drawing.Graphics.DrawString%2A> vektör görüntüleri, ızgara görüntüleri ve metin görüntüleme. A <xref:System.Drawing.Graphics> nesne kalitesini ve çizilir öğeleri yönünü etkileyen çeşitli özellikler de vardır. Örneğin, yumuşatma modu özelliği çizgiler ve eğrilerle düzgünleştirme uygulanır ve dünya dönüşümü özelliği konum ve dönüş çizilir öğelerinin etkilediğini olup olmadığını belirler.  
  
 A <xref:System.Drawing.Graphics> nesne belirli görüntüleme cihazı ile ilişkili değil. Kullandığınızda, bir <xref:System.Drawing.Graphics> bir pencerede çizmek için nesne <xref:System.Drawing.Graphics> nesne bu belirli pencere ile ilişkili değil de.  
  
 A <xref:System.Drawing.Graphics> nesne zorlayıcı bir kapsayıcı olarak çizim etkileyen özellikler kümesi tutan olduğundan ve cihaza özgü bilgileri bağlı. Var olan içindeki ikincil bir kapsayıcı oluşturabilirsiniz <xref:System.Drawing.Graphics> çağırarak nesne <xref:System.Drawing.Graphics.BeginContainer%2A> yöntemi, <xref:System.Drawing.Graphics> nesnesi.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bir Grafik Nesnesinin Durumunu Yönetme](../../../../docs/framework/winforms/advanced/managing-the-state-of-a-graphics-object.md)  
 Açıklar kalitesi ayarları, kırpma alanı ve dönüşümleri, nasıl yönettiğini bir <xref:System.Drawing.Graphics> nesnesi.  
  
 [İç İçe Grafik Kapsayıcılarını Kullanma](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)  
 Kapsayıcıları durumunu denetlemek için nasıl kullanılacağını gösterir <xref:System.Drawing.Graphics> nesnesi.
