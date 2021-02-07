---
description: "Hakkında daha fazla bilgi edinin: nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma"
title: Visual Studio 'da LINQ to DataSet projesi oluşturma
ms.date: 08/15/2018
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
ms.openlocfilehash: 4ab626ddaa27780759df95462faac366be8beeff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723835"
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Nasıl yapılır: Visual Studio 'da LINQ to DataSet projesi oluşturma

Farklı LINQ Projesi türleri arasında bazı derleme başvuruları ve içeri aktarılan ad alanları (Visual Basic [) veya yönergeler](../../../csharp/language-reference/keywords/using-directive.md) (C#) gerekir. LINQ için en düşük gereksinim, *System.Core.dll* bir başvurudur ve için bir `using` yönergedir <xref:System.Linq> .

Bu gereksinimler, Visual Studio 2017 veya sonraki bir sürümde yeni bir C# konsol uygulaması projesi oluşturduğunuzda varsayılan olarak sağlanır. Bir projeyi Visual Studio 'nun önceki bir sürümünden yükseltiyorsanız, bu LINQ ile ilgili başvuruları el ile sağlamanız gerekebilir.

LINQ to DataSet *System.Data.dll* ve *System.Data.DataSetExtensions.dll* için iki ek başvuru gerektirir.

> [!NOTE]
> Bir komut isteminden derleme yapıyorsanız,%ProgramFiles%\Reference, bir LINQ ile ilgili DLL 'Leri/ *Vn\microsoft\framework\v3.5* içinde el ile başvurmanız gerekir.

## <a name="to-enable-linq-to-dataset-functionality"></a>LINQ to DataSet işlevselliği etkinleştirmek için

Mevcut bir projede LINQ to DataSet işlevselliği etkinleştirmek için bu adımları izleyin.

1. **System. Core**, **System. Data** ve **System. Data. datasecımsions**'e başvurular ekleyin.

   **Çözüm Gezgini**, **Başvurular** düğümüne sağ tıklayın ve **Başvuru Ekle**' yi seçin. **Başvuru Yöneticisi** iletişim kutusunda, **System. Core**, **System. Data** ve **System. Data. Datasecccccdentitysions öğelerini** seçin. **Tamam**’ı seçin.

1. **System. Data** ve **System. LINQ** için [using](../../../csharp/language-reference/keywords/using-directive.md) yönergelerini (veya Visual Basic [deyimlerini içeri aktarır](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) ) ekleyin.

   ```csharp
   using System.Data;
   using System.Linq;
   ```

1. İsteğe bağlı olarak, `using` `Imports` veritabanına nasıl bağlandığınıza bağlı olarak **System. Data. Common** veya **System. Data. SqlClient** için bir yönerge (veya bildiri) ekleyin.

## <a name="see-also"></a>Ayrıca bkz.

- [LINQ to DataSet kullanmaya başlayın](getting-started-linq-to-dataset.md)
