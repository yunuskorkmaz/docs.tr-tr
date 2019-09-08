---
title: Visual Studio 'Da LINQ to DataSet projesi oluşturma
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 8b905c65575c3c567459d843b2a5d1606bc63228
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70783768"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Nasıl yapılır: Visual Studio 'Da LINQ to DataSet projesi oluşturma

Farklı LINQ Projesi türleri arasında bazı derleme başvuruları ve içeri aktarılan ad alanları (Visual Basic) veya [](../../../csharp/language-reference/keywords/using-directive.md) yönergeleri (C#) kullanılması gerekir. LINQ için en düşük gereksinim *System. Core. dll* ve için `using` <xref:System.Linq>bir yönergedir.

Bu gereksinimler, Visual Studio 2017 ' de yeni C# bir konsol uygulama projesi oluşturursanız varsayılan olarak sağlanır. Bir projeyi Visual Studio 'nun önceki bir sürümünden yükseltiyorsanız, bu LINQ ile ilgili başvuruları el ile sağlamanız gerekebilir.

LINQ to DataSet, *System. Data. dll* ve *System. Data. Datase, sions. dll*' ye iki ek başvuru gerektirir.

> [!NOTE]
> Bir komut isteminden derleme yapıyorsanız,%ProgramFiles%\Reference, bir LINQ ile ilgili DLL 'Leri/ *Vn\microsoft\framework\v3.5*içinde el ile başvurmanız gerekir.

## <a name="to-enable-linq-to-dataset-functionality"></a>LINQ to DataSet işlevselliği etkinleştirmek için

Mevcut bir projede LINQ to DataSet işlevselliği etkinleştirmek için bu adımları izleyin.

1. **System. Core**, **System. Data**ve **System. Data. datasecımsions**'e başvurular ekleyin.

   **Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin. **Başvuru Yöneticisi** iletişim kutusunda, **System. Core**, **System. Data**ve **System. Data. Datasecccccdentitysions öğelerini**seçin. **Tamam**’ı seçin.

1. **System. Data** ve **System. LINQ**için [using](../../../csharp/language-reference/keywords/using-directive.md) yönergelerini (veya Visual Basic [deyimlerini içeri aktarır](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ) ekleyin.

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. İsteğe bağlı olarak, `using` veritabanına nasıl bağlandığınıza bağlı olarak **System. Data. Common** veya **System. Data. SqlClient**için bir yönerge (veya `Imports` bildiri) ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet kullanmaya başlayın](getting-started-linq-to-dataset.md)
