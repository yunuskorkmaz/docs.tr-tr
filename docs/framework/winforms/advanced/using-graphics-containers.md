---
title: Grafik Kapsayıcıları Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], using containers
- graphics containers
- examples [Windows Forms], graphics containers
ms.assetid: 74632f91-cefa-4f51-ab7c-f9ac91942caf
ms.openlocfilehash: cfad7254057a31ea8268784cd4b6849850f3e2aa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61766161"
---
# <a name="using-graphics-containers"></a>Grafik Kapsayıcıları Kullanma
A <xref:System.Drawing.Graphics> nesne yöntemleri gibi sağlar <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, ve <xref:System.Drawing.Graphics.DrawString%2A> vektör görüntüleri, tarama görüntü ve metin gösterme. A <xref:System.Drawing.Graphics> nesne çizilir öğeleri yönünü ve kalite etkileyen çeşitli özellikleri de vardır. Örneğin, yumuşatma modu özelliği için çizgiler ve eğrilerle düzgünleştirme uygulanır ve konum ve döndürme çizilir öğelerinin dünya dönüştürme özelliğini etkiler olup olmadığını belirler.  
  
 A <xref:System.Drawing.Graphics> nesne belirli bir görüntü cihazı ile ilişkili değil. Kullandığınızda, bir <xref:System.Drawing.Graphics> bir pencerede çizmek için nesne <xref:System.Drawing.Graphics> nesnedir Ayrıca, belirli bir pencere ile ilişkili.  
  
 A <xref:System.Drawing.Graphics> nesne düşünülebilir bir kapsayıcı gibi çizim etkileyen özellikler kümesi tutmadığından ve cihaza özgü bilgiler için bağlıdır. İçinde mevcut bir ikincil bir kapsayıcı oluşturduğunuz <xref:System.Drawing.Graphics> çağırarak <xref:System.Drawing.Graphics.BeginContainer%2A> yöntem <xref:System.Drawing.Graphics> nesne.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [Bir Grafik Nesnesinin Durumunu Yönetme](managing-the-state-of-a-graphics-object.md)  
 Açıklar kalite ayarları, kırpma alan ve dönüşümleri yönetme bir <xref:System.Drawing.Graphics> nesne.  
  
 [İç İçe Grafik Kapsayıcılarını Kullanma](using-nested-graphics-containers.md)  
 Durumu denetlemek için kapsayıcıları kullanmayı gösterir <xref:System.Drawing.Graphics> nesne.
