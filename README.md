# CSCI527
CSCI527 Mahjong Agent Repo

## AI Documentation
> A guide to create AI agent

```python
ai.erase_state()
```
erase_state is called in table.py for round initialization

```python
ai.init_hand()
```
init_hand is called in player.py for hand initialization

```python
ai.draw_tile(tile_136)
```
- tile_136: list of int, 136_array. Generate from TilesConverter.string_to_136_array

```python
tile_to_discard, with_riichi = ai.discard_tile(discard_tile)
```
- discard_tile: int, 136_tile. Generated from TilesConverter.string_to_136_array[0]. A previous suggestion from ai.try_to_call_meld() or riichi rules. Can be none.
- tile_to_discard: int, 136_tile. Generated from TilesConverter.string_to_136_array[0].
- with_riichi: bool. Should call riichi after tile discard.

```python
kan_type = ai.kan.should_call_kan(tile, open_kan, from_riichi)
```
- tile: int, 136_tile. Generated from TilesConverter.string_to_136_array[0].
- open_kan: bool. False for 暗杠.
- from_riichi: bool. Already riichi.
- return: None for do not kan. kan_type == mahjong.meld.SHOUMINKAN for "upgraded pon to kan", else for "call a closed kan set".

```python
ai.should_call_win(tile, is_tsumo, enemy_seat, is_chankan)
```
- tile: int, 136_tile. Generated from TilesConverter.string_to_136_array[0].
- is_tsumo: bool. True for 自摸.
- enemy_seat: int. Generated from player.table.get_players_sorted_by_scores()[x] 放铳者
- is_chankan: bool. True for 抢杠.
- return: bool. Should call win.

```python
ai.should_call_kyuushu_kyuuhai()
```
- return: bool. Should call kyuushu_kyuuhai(九种九牌).

```python
meld, discard_option = self.ai.try_to_call_meld(tile, is_kamicha_discard)
```
- tile: int, 136_tile. Generated from TilesConverter.string_to_136_array[0].
- is_kamicha_discard： bool. Discard tile is from opponent on the left(上家).
- meld: meld==none for skip. meld.type=mahjong.meld.CHI\PON, meld.tiles=list of int, size of 3, 136_array.
- discard_option: int, 136_tile. Tile to discard.

```python
ai.enemy_called_riichi(player_seat)
```
- player_seat: int.
