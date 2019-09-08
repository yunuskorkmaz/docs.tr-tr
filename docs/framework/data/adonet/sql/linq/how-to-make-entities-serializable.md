---
title: 'Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 40a0b4d5a49f88af1bedcbefdd117f6c000b791d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793557"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="aa381-102">Nasıl yapılır: Varlıkları Serileştirilebilir Hale Getirme</span><span class="sxs-lookup"><span data-stu-id="aa381-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="aa381-103">Kodunuzu oluştururken varlıkları seri hale getirilebilir hale getirebilirsiniz.</span><span class="sxs-lookup"><span data-stu-id="aa381-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="aa381-104">Varlık sınıfları özniteliğiyle ve <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> özniteliğiyle birlikte sütunlar halinde tasarlanmalıdır.</span><span class="sxs-lookup"><span data-stu-id="aa381-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="aa381-105">Visual Studio kullanan geliştiriciler bu amaçla Nesne İlişkisel Tasarımcısı kullanabilir.</span><span class="sxs-lookup"><span data-stu-id="aa381-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="aa381-106">SqlMetal komut satırı aracını kullanıyorsanız, **/Serialization** seçeneğini `unidirectional` bağımsız değişkeniyle birlikte kullanın.</span><span class="sxs-lookup"><span data-stu-id="aa381-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="aa381-107">Daha fazla bilgi için bkz. [SqlMetal. exe (kod üretme aracı)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="aa381-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa381-108">Örnek</span><span class="sxs-lookup"><span data-stu-id="aa381-108">Example</span></span>  
 <span data-ttu-id="aa381-109">Aşağıdaki SQLMetal komut satırları, serileştirilebilir varlıkları olan dosyaları oluşturur.</span><span class="sxs-lookup"><span data-stu-id="aa381-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="aa381-110">Ayrıca bkz.</span><span class="sxs-lookup"><span data-stu-id="aa381-110">See also</span></span>

- [<span data-ttu-id="aa381-111">Serileştirme</span><span class="sxs-lookup"><span data-stu-id="aa381-111">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="aa381-112">Nesne Modeli Oluşturma</span><span class="sxs-lookup"><span data-stu-id="aa381-112">Creating the Object Model</span></span>](creating-the-object-model.md)
