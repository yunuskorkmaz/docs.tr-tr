---
title: Visual Studio 'da LINQ to DataSet projesi oluşturma
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 91032766248b11e51b90aa788b1c64c140347c25
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802020"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma

Farklı LINQ Projesi türleri arasında bazı derleme başvuruları ve içeri aktarılan ad alanları (Visual Basic) veya [](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri (C#) kullanılması gerekir. LINQ için en düşük gereksinim, *System. Core. dll* ve <xref:System.Linq>için bir `using` yönergesine başvurudur.

Bu gereksinimler, Visual Studio 2017 veya sonraki bir sürümde yeni C# bir konsol uygulama projesi oluşturursanız varsayılan olarak sağlanır. Bir projeyi Visual Studio 'nun önceki bir sürümünden yükseltiyorsanız, bu LINQ ile ilgili başvuruları el ile sağlamanız gerekebilir.

LINQ to DataSet, *System. Data. dll* ve *System. Data. Datase, sions. dll*' ye iki ek başvuru gerektirir.

> [!NOTE]
> Bir komut isteminden derleme yapıyorsanız,%ProgramFiles%\Reference, bir LINQ ile ilgili DLL 'Leri/ *Vn\microsoft\framework\v3.5*içinde el ile başvurmanız gerekir.

## <a name="to-enable-linq-to-dataset-functionality"></a>LINQ to DataSet işlevselliği etkinleştirmek için

Mevcut bir projede LINQ to DataSet işlevselliği etkinleştirmek için bu adımları izleyin.

1. **System. Core**, **System. Data**ve **System. Data. datasecımsions**'e başvurular ekleyin.

   **Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin. **Başvuru Yöneticisi** iletişim kutusunda, **System. Core**, **System. Data**ve **System. Data. Datasecccccdentitysions öğelerini**seçin. Seçin **Tamam**.

1. **System. Data** ve **System. LINQ**için [using](../../../csharp/language-reference/keywords/using-directive.md) yönergelerini (veya Visual Basic [deyimlerini içeri aktarır](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ) ekleyin.

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. İsteğe bağlı olarak, veritabanına nasıl bağlandığınıza bağlı olarak **System. Data. Common** veya **System. Data. SqlClient**için `using` yönergesini (veya `Imports` bildirisini) ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet kullanmaya başlayın](getting-started-linq-to-dataset.md)
