---
title: İki Kez Arabelleğe Almayı Kullanma
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [Windows Forms], double buffering
- double buffering
- flicker [Windows Forms], reducing in Windows Forms
- buffering [Windows Forms], double buffering
ms.assetid: dc484e33-7101-4e4b-ada5-d3c96155fbcd
ms.openlocfilehash: ac6c9b7f2cc1fea86a75eaaf4a2dde1ea60e4f40
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61777162"
---
# <a name="using-double-buffering"></a>İki Kez Arabelleğe Almayı Kullanma
İki kez arabelleğe alınan grafikler, karmaşık boyama işlemler içeren, uygulamalarınızda titreşimi azaltmak için kullanabilirsiniz. .NET Framework iki kez arabelleğe alma için yerleşik destek içerir veya yönetebilir ve grafikleri elle işleme.  
  
## <a name="in-this-section"></a>Bu Bölümde  
 [İki Kez Arabelleğe Alınan Grafikler](double-buffered-graphics.md)  
 Çift arabelleğe alma kavram ve ana hatlarını .NET Framework Destek sunuyor.  
  
 [Nasıl yapılır: Formlar ve denetimler için çift arabelleğe alma ile grafik titreşimini azaltma](how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls.md)  
 Varsayılan .NET Framework Destek arabelleğe çift nasıl yapılacağı açıklanır.  
  
 [Nasıl yapılır: Arabelleğe alınan grafikleri elle yönetme](how-to-manually-manage-buffered-graphics.md)  
 Uygulamalarda iki kez arabelleğe alma yönetme işlemini göstermektedir.  
  
 [Nasıl yapılır: Arabelleğe alınan grafikleri elle işleme](how-to-manually-render-buffered-graphics.md)  
 İki kez arabelleğe alınan grafikler nasıl oluşturulacağını gösterir.  
  
## <a name="reference"></a>Başvuru  
 <xref:System.Windows.Forms.Control.SetStyle%2A> ,  
 Denetim yöntemi iki kez arabelleğe almayı sağlar.  
  
 <xref:System.Drawing.BufferedGraphicsContext> ,  
 Grafik arabellekleri oluşturmak için yöntemleri sağlar.  
  
 <xref:System.Drawing.BufferedGraphicsManager>  
 Bir uygulama etki alanı için arabelleğe alınan grafikleri bağlam erişim sağlar.
